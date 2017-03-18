# OxygenXML Web Author Docker Container

This container sets up an OxygenXML Web Author server under Tomcat.
It uses a demo license by default.

You can set it up with your own license by replacing the `license.properties` with your own license details.

*NOTE:* The required `oxygenxml-web-author.war` file is not included in the files managed in git. You'll need to download your own copy from the OxygenXML Web site (https://www.oxygenxml.com/xml_web_author/download_oxygenxml_web_author.html?os=WebApplicationArchive) and put it in the same directory as the `Dockerfile`.

The `tomcat-users.xml` and `settings.xml` files set up a default user for logging into the OxygenXML Wev Author administration page: oxyadmin with password "password".

This container is set up so that no additional configuration is required once you start the container.

For a production system you'd probably want to make the apps WEB-INF directory into a volume so you can modify the configuration dynamically and persist it as well. There may be other configuration files or temp files that should be persisted in a volume.
