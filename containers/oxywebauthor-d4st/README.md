# OxygenXML Web Author Docker Container

This container sets up an OxygenXML Web Author server under Tomcat.
It uses a demo license by default.

You can set it up with your own license by replacing the `license.properties` with your own license details.

The `tomcat-users.xml` and `settings.xml` files set up a default user for logging into the OxygenXML Wev Author administration page: oxyadmin with password "password".

This container is set up so that no additional configuration is required once you start the container.

For a production system you'd probably want to make the apps WEB-INF directory into a volume so you can modify the configuration dynamically and persist it as well. There may be other configuration files or temp files that should be persisted in a volume.
