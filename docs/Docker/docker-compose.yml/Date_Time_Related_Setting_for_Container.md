##Under the service of the container which you want to change the timezone, add:

    services:
      [service_name]:
        environment:
          TZ: "America/Toronto"