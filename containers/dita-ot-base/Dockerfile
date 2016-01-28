FROM java:8
MAINTAINER Eliot Kimber "ekimber@contrext.com"
# Make directories for later use
ENV CATALOG_DIR /opt/dita-ot/catalogs
RUN mkdir -p /opt/dita-ot/catalogs
RUN chmod -R a+rwx $CATALOG_DIR

RUN useradd -u 5555 -ms /bin/bash dita-ot

ENV HOME /home/dita-ot
ENV DITA_HOME $HOME/DITA-OT
# For OT 2.x the ant script is in the top-level bin/ dir
ENV ANT_HOME $DITA_HOME
ENV PATH $ANT_HOME/bin:$DITA_HOME:$PATH
USER 5555
WORKDIR $HOME
# This URL does not seem to be reliable.
#RUN wget -c {put github package URL here}
# For doing lots of builds to avoid fetching each time.
COPY dita-ot-2.2.0.zip /home/dita-ot/dita-ot.zip
RUN unzip dita-ot.zip && \
    rm dita-ot.zip
# Use a consistent name for the OT so we don't have to worry about it
RUN mv dita-ot-2.2.0 DITA-OT
# Set execution permissions on ant/bin directory
RUN chmod a+rwx $DITA_HOME/bin/* 
# Put the bin directory in the path:
# For OT 2.x:
ENV PATH $HOME/DITA-OT/bin:$PATH
# Copy the catalog and plugins directory to a volume
# so other containers can use it.
RUN cp $DITA_HOME/catalog-dita.xml $CATALOG_DIR/catalog-dita.xml 
RUN ln -s $DITA_HOME/plugins $CATALOG_DIR/plugins 
# Provide a way for the OT to access user data:
VOLUME $CATALOG_DIR
VOLUME /opt/dita-ot/userdata
WORKDIR $DITA_HOME
#
# NOTE For OT 2.x, the dita command manages the Java classpath.
#
# End of Dockerfile
#