FROM java:8
MAINTAINER Eliot Kimber "ekimber@contrext.com"
# Make directories for later use
ENV CATALOG_DIR /opt/dita-ot/catalogs
RUN mkdir -p /opt/dita-ot/catalogs
RUN chmod -R a+rwx $CATALOG_DIR

RUN useradd -u 5555 -ms /bin/bash dita-ot

ENV HOME /home/dita-ot
# For OT 1.x:
ENV DITA_HOME $HOME/DITA-OT
ENV ANT_HOME $DITA_HOME/tools/ant
ENV PATH $ANT_HOME/bin:$DITA_HOME:$PATH
USER 5555
WORKDIR $HOME
# This URL does not seem to be reliable.
#RUN wget -c http://sourceforge.net/projects/dita-ot/files/DITA-OT%20Stable%20Release/DITA%20Open%20Toolkit%201.8/DITA-OT1.8.5_full_easy_install_bin.zip 
# For doing lots of builds to avoid fetching each time.
COPY DITA-OT1.8.5_full_easy_install_bin.zip /home/dita-ot/DITA-OT1.8.5_full_easy_install_bin.zip
RUN unzip DITA-OT1.8.5_full_easy_install_bin.zip && \
    rm DITA-OT1.8.5_full_easy_install_bin.zip
# Use a consistent name for the OT so we don't have to worry about it
RUN mv DITA-OT1.8.5 DITA-OT
# Set execution permissions on ant/bin directory
RUN chmod a+rwx $DITA_HOME/startcmd.sh $ANT_HOME/bin/ant 
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
# Set up the Java classpath as defined in startcmd.sh:
ENV CLASSPATH $DITA_HOME/lib/dost.jar:\
$DITA_HOME/lib:\
$DITA_HOME/lib/commons-codec-1.4.jar:\
$DITA_HOME/lib/resolver.jar:\
$DITA_HOME/lib/icu4j.jar:\
$DITA_HOME/lib/xercesImpl.jar:\
$DITA_HOME/lib/xml-apis.jar:\
$DITA_HOME/lib/saxon/saxon9.jar:\
$DITA_HOME/lib/saxon/saxon9-dom.jar
#
# End of Dockerfile
#