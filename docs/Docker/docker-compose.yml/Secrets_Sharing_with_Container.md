##Under the service of the container which you want to share the secrets, add:

    services:
      [service_name]:
        environment:
          SSH_AUTH_SOCK: /ssh-agent
        volumes:
          - $SSH_AUTH_SOCK:/ssh-agent # Forward local machine SSH key to docker