* OS: Linux Mint 19 Tara or Ubuntu 18.04 Bionic Beaver

##I. Install Jenkins on Linux

###1. This is the Debian package repository of Jenkins to automate installation and upgrade. 
To use this repository, first add the key to your system:
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
```

Then add the following entry in your /etc/apt/sources.list:
```
deb https://pkg.jenkins.io/debian-stable binary/
```

Update your local package index, then finally install Jenkins:
```
sudo apt-get update
sudo apt-get install jenkins
```

###2. Check Jenkins status
```
$ sudo service jenkins status

● jenkins.service - LSB: Start Jenkins at boot time
   Loaded: loaded (/etc/init.d/jenkins; generated)
   Active: active (exited) since Wed 2019-06-19 09:10:03 EDT; 2s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 24191 ExecStart=/etc/init.d/jenkins start (code=exited, status=0/SUCCESS)

Jun 19 09:10:01 e580-hluo systemd[1]: Starting LSB: Start Jenkins at boot time...
Jun 19 09:10:01 e580-hluo jenkins[24191]: Correct java version found
Jun 19 09:10:02 e580-hluo jenkins[24191]:  * Starting Jenkins Automation Server jenkins
Jun 19 09:10:02 e580-hluo su[24244]: Successful su for hluo by root
Jun 19 09:10:02 e580-hluo su[24244]: + ??? root:hluo
Jun 19 09:10:02 e580-hluo su[24244]: pam_unix(su:session): session opened for user hluo by (uid=0)
Jun 19 09:10:02 e580-hluo su[24244]: pam_unix(su:session): session closed for user hluo
Jun 19 09:10:03 e580-hluo jenkins[24191]:    ...done.
Jun 19 09:10:03 e580-hluo systemd[1]: Started LSB: Start Jenkins at boot time.
```

###3. Check Jenkins on web browser, use http://localhost:8080/

##II. Change Username for Running Jenkins
### 1. Update `/etc/init.d/jenkins`
```
#!/bin/bash
# /etc/init.d/jenkins
# debian-compatible jenkins startup script.
# Amelia A Lewis <alewis@ibco.com>
#
### BEGIN INIT INFO
# Provides:          jenkins
# Required-Start:    $remote_fs $syslog $network
# Required-Stop:     $remote_fs $syslog $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start Jenkins at boot time
# Description:       Controls Jenkins Automation Server
### END INIT INFO

PATH=/bin:/usr/bin:/sbin:/usr/sbin

DESC="Jenkins Automation Server"
NAME=jenkins
###########################################################
### Added below line to allow user alternative username ###
###########################################################
USERNAME=hluo
SCRIPTNAME=/etc/init.d/$NAME

[ -r /etc/default/$NAME ] && . /etc/default/$NAME

#DAEMON=$JENKINS_SH
DAEMON=/usr/bin/daemon
#DAEMON_ARGS="--name=$NAME --inherit --env=JENKINS_HOME=$JENKINS_HOME --output=$JENKINS_LOG --pidfile=$PIDFILE"
###########################################################
### Backup old line and modify daemon execution user    ###
###########################################################
DAEMON_ARGS="--name=$USERNAME --inherit --env=JENKINS_HOME=$JENKINS_HOME --output=$JENKINS_LOG --pidfile=$PIDFILE"

JAVA=`type -p java`

if [ -n "$UMASK" ]; then
    DAEMON_ARGS="$DAEMON_ARGS --umask=$UMASK"
fi
if [ "$JENKINS_ENABLE_ACCESS_LOG" = "yes" ]; then
    JENKINS_ARGS="$JENKINS_ARGS --accessLoggerClassName=winstone.accesslog.SimpleAccessLogger --simpleAccessLogger.format=combined --simpleAccessLogger.file=/var/log/$NAME/access_log"
fi

SU=/bin/su

# Exit if the package is not installed
if [ ! -x "$DAEMON" ]; then
    echo "daemon package not installed" >&2
    exit 1
fi

# Exit if not supposed to run standalone
if [ "$RUN_STANDALONE" = "false" ]; then
    echo "Not configured to run standalone" >&2
    exit 1
fi

# Make sure there exists a java executable, it may not be allways the case
if [ -z "$JAVA" ]; then
    echo "ERROR: No Java executable found in current PATH: $PATH" >&2
    echo "If you actually have java installed on the system make sure the executable is in the aforementioned path and that 'type -p java' returns the java executable path" >&2
    exit 1
fi

# Which Java versions can be used to run Jenkins
JAVA_ALLOWED_VERSIONS=( "18" "110" )
# Work out the JAVA version we are working with:
JAVA_VERSION=$($JAVA -version 2>&1 | sed -n ';s/.* version "\(.*\)\.\(.*\)\..*".*/\1\2/p;')

if [[ ${JAVA_ALLOWED_VERSIONS[*]} =~ "$JAVA_VERSION" ]]; then
    echo "Correct java version found" >&2
else
    echo "Found an incorrect Java version" >&2
    echo "Java version found:" >&2
    echo $($JAVA -version) >&2
    echo "Aborting" >&2
    exit 1
fi

# load environments
if [ -r /etc/default/locale ]; then
  . /etc/default/locale
  export LANG LANGUAGE
elif [ -r /etc/environment ]; then
  . /etc/environment
  export LANG LANGUAGE
fi

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Make sure we run as root, since setting the max open files through
# ulimit requires root access
if [ `id -u` -ne 0 ]; then
    echo "The $NAME init script can only be run as root"
    exit 1
fi


check_tcp_port() {
    local service=$1
    local assigned=$2
    local default=$3
    local assigned_address=$4
    local default_address=$5

    if [ -n "$assigned" ]; then
        port=$assigned
    else
        port=$default
    fi

    if [ -n "$assigned_address" ]; then
        address=$assigned_address
    else
        address=$default_address
    fi

    count=`netstat --listen --numeric-ports | grep $address\:$port[[:space:]] | grep -c . `

    if [ $count -ne 0 ]; then
        echo "The selected $service port ($port) on address $address seems to be in use by another program "
        echo "Please select another address/port combination to use for $NAME"
        return 1
    fi
}

#
# Function that starts the daemon/service
#
do_start()
{
    # the default location is /var/run/jenkins/jenkins.pid but the parent directory needs to be created
    mkdir `dirname $PIDFILE` > /dev/null 2>&1 || true
    chown $JENKINS_USER `dirname $PIDFILE`
    # Return
    #   0 if daemon has been started
    #   1 if daemon was already running
    #   2 if daemon could not be started
    $DAEMON $DAEMON_ARGS --running && return 1

    # Verify that the jenkins port is not already in use, winstone does not exit
    # even for BindException
    check_tcp_port "http" "$HTTP_PORT" "8080" "$HTTP_HOST" "0.0.0.0" || return 2

    # If the var MAXOPENFILES is enabled in /etc/default/jenkins then set the max open files to the
    # proper value
    if [ -n "$MAXOPENFILES" ]; then
        [ "$VERBOSE" != no ] && echo Setting up max open files limit to $MAXOPENFILES
        ulimit -n $MAXOPENFILES
    fi

    # notify of explicit umask
    if [ -n "$UMASK" ]; then
        [ "$VERBOSE" != no ] && echo Setting umask to $UMASK
    fi

    # --user in daemon doesn't prepare environment variables like HOME, USER, LOGNAME or USERNAME,
    # so we let su do so for us now
    $SU -l $JENKINS_USER --shell=/bin/bash -c "$DAEMON $DAEMON_ARGS -- $JAVA $JAVA_ARGS -jar $JENKINS_WAR $JENKINS_ARGS" || return 2
}


#
# Verify that all jenkins processes have been shutdown
# and if not, then do killall for them
#
get_running()
{
    return `ps -U $JENKINS_USER --no-headers -f | egrep -e '(java)' | grep -v defunct | grep -c . `
}

force_stop()
{
    get_running
    if [ $? -ne 0 ]; then
	killall -u $JENKINS_USER java daemon || return 3
    fi
}

# Get the status of the daemon process
get_daemon_status()
{
    $DAEMON $DAEMON_ARGS --running || return 1
}


#
# Function that stops the daemon/service
#
do_stop()
{
    # Return
    #   0 if daemon has been stopped
    #   1 if daemon was already stopped
    #   2 if daemon could not be stopped
    #   other if a failure occurred
    get_daemon_status
    case "$?" in
	0)
	    $DAEMON $DAEMON_ARGS --stop || return 2
        # wait for the process to really terminate
        for n in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20; do
            sleep 1
            $DAEMON $DAEMON_ARGS --running || break
        done
        if get_daemon_status; then
	        force_stop || return 3
        fi
	    ;;
	*)
	    force_stop || return 3
	    ;;
    esac

    # Many daemons don't delete their pidfiles when they exit.
    rm -f $PIDFILE
    return 0
}

# Verify the process did in fact start successfully and didn't just bomb out
do_check_started_ok() {
    sleep 1
    if [ "$1" -ne "0" ]; then return $1; fi
    get_running
    if [ "$?" -eq "0" ]; then
        return 2
    else
        return 0
    fi
}

case "$1" in
  start)
    log_daemon_msg "Starting $DESC" "$NAME"
    do_start
    START_STATUS="$?"
    do_check_started_ok "$START_STATUS"
    case "$?" in
        0|1) log_end_msg 0 ;;
        2) log_end_msg 1 ; exit 7 ;;
    esac
    ;;
  stop)
    log_daemon_msg "Stopping $DESC" "$NAME"
    do_stop
    case "$?" in
        0|1) log_end_msg 0 ;;
        2) log_end_msg 1 ; exit 100 ;;
    esac
    ;;
  restart|force-reload)
    #
    # If the "reload" option is implemented then remove the
    # 'force-reload' alias
    #
    log_daemon_msg "Restarting $DESC" "$NAME"
    do_stop
    case "$?" in
      0|1)
        do_start
        START_STATUS="$?"
        sleep 1
        do_check_started_ok "$START_STATUS"
        case "$?" in
          0) log_end_msg 0 ;;
          1) log_end_msg 1 ; exit 100 ;; # Old process is still running
          *) log_end_msg 1 ; exit 100 ;; # Failed to start
        esac
        ;;
      *)
  	# Failed to stop
	log_end_msg 1
	;;
    esac
    ;;
  status)
	get_daemon_status
	case "$?" in
	 0)
		echo "$DESC is running with the pid `cat $PIDFILE`"
		rc=0
		;;
	*)
		get_running
		procs=$?
		if [ $procs -eq 0 ]; then
			echo -n "$DESC is not running"
			if [ -f $PIDFILE ]; then
				echo ", but the pidfile ($PIDFILE) still exists"
				rc=1
			else
				echo
				rc=3
			fi

		else
			echo "$procs instances of jenkins are running at the moment"
			echo "but the pidfile $PIDFILE is missing"
			rc=0
		fi

		exit $rc
		;;
	esac
	;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|status|restart|force-reload}" >&2
    exit 3
    ;;
esac

exit 0
```


### 2. Update `/etc/default/jenkins`
```
# defaults for Jenkins automation server

# pulled in from the init script; makes things easier.
NAME=jenkins
###########################################################
### Added below line to allow user alternative username ###
###########################################################
USERNAME=hluo

# arguments to pass to java

# Allow graphs etc. to work even when an X server is present
JAVA_ARGS="-Djava.awt.headless=true"

#JAVA_ARGS="-Xmx256m"

# make jenkins listen on IPv4 address
#JAVA_ARGS="-Djava.net.preferIPv4Stack=true"

PIDFILE=/var/run/$NAME/$NAME.pid

# user and group to be invoked as (default to jenkins)
#JENKINS_USER=$NAME
###########################################################
### Backup old line and modify execution user           ###
###########################################################
JENKINS_USER=$USERNAME
JENKINS_GROUP=$NAME

# location of the jenkins war file
JENKINS_WAR=/usr/share/$NAME/$NAME.war

# jenkins home location
JENKINS_HOME=/var/lib/$NAME

# set this to false if you don't want Jenkins to run by itself
# in this set up, you are expected to provide a servlet container
# to host jenkins.
RUN_STANDALONE=true

# log location.  this may be a syslog facility.priority
JENKINS_LOG=/var/log/$NAME/$NAME.log
#JENKINS_LOG=daemon.info

# Whether to enable web access logging or not.
# Set to "yes" to enable logging to /var/log/$NAME/access_log
#JENKINS_ENABLE_ACCESS_LOG="no"
JENKINS_ENABLE_ACCESS_LOG="yes"

# OS LIMITS SETUP
#   comment this out to observe /etc/security/limits.conf
#   this is on by default because http://github.com/jenkinsci/jenkins/commit/2fb288474e980d0e7ff9c4a3b768874835a3e92e
#   reported that Ubuntu's PAM configuration doesn't include pam_limits.so, and as a result the # of file
#   descriptors are forced to 1024 regardless of /etc/security/limits.conf
MAXOPENFILES=8192

# set the umask to control permission bits of files that Jenkins creates.
#   027 makes files read-only for group and inaccessible for others, which some security sensitive users
#   might consider benefitial, especially if Jenkins runs in a box that's used for multiple purposes.
#   Beware that 027 permission would interfere with sudo scripts that run on the master (JENKINS-25065.)
#
#   Note also that the particularly sensitive part of $JENKINS_HOME (such as credentials) are always
#   written without 'others' access. So the umask values only affect job configuration, build records,
#   that sort of things.
#
#   If commented out, the value from the OS is inherited,  which is normally 022 (as of Ubuntu 12.04,
#   by default umask comes from pam_umask(8) and /etc/login.defs

# UMASK=027

# port for HTTP connector (default 8080; disable with -1)
HTTP_PORT=8080


# servlet context, important if you want to use apache proxying
PREFIX=/$NAME

# arguments to pass to jenkins.
# --javahome=$JAVA_HOME
# --httpListenAddress=$HTTP_HOST (default 0.0.0.0)
# --httpPort=$HTTP_PORT (default 8080; disable with -1)
# --httpsPort=$HTTP_PORT
# --argumentsRealm.passwd.$ADMIN_USER=[password]
# --argumentsRealm.roles.$ADMIN_USER=admin
# --webroot=~/.jenkins/war
# --prefix=$PREFIX

JENKINS_ARGS="--webroot=/var/cache/$NAME/war --httpPort=$HTTP_PORT"
```
###3. Update folders and files owner
```
$ sudo chown -R hluo:jenkins /var/lib/jenkins
$ sudo chown -R hluo:jenkins /var/cache/jenkins
$ sudo chown -R hluo:jenkins /var/log/jenkins
```

###4. Reload daemon module and restart Jenkins
```
$ systemctl daemon-reload

$ sudo service jenkins restart
```
##III. Initial configure Jenkins
###1. Get content of `/var/lib/jenkins/secrets/initialAdminPassword` for first login

###2. Install plugins and add a new admin user account
 
###3. Login with new account and you should see the Jenkins dashboard