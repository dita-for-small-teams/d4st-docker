FROM java:8
MAINTAINER Eliot Kimber "ekimber@contrext.com"
#
# Container for the DFST BaseX-based Link Manager web
# application. 
#
# This container separates the Web app source from
# the main BaseX container to make it easier to update
# the Web app.
#
# Add the DFST link manager web app from
# github:

RUN wget https://github.com/dita-for-small-teams/dfst-linkmgmt-basex/archive/develop.zip && \
  unzip develop.zip && \
  rm develop.zip
RUN mkdir /webapp && \
    mkdir /webapp/static && \
    mkdir /webapp/dba && \
    mkdir /repo 
RUN cp dfst-linkmgmt-basex-develop/webapp/*.xqm /webapp/ && \
    cp -r dfst-linkmgmt-basex-develop/webapp/static/* /webapp/static/ && \
    cp -r dfst-linkmgmt-basex-develop/modules/dba /webapp/dba/modules && \
    cp -r dfst-linkmgmt-basex-develop/modules/* /repo

# 
# Define the volumes that will be used in place of the base BaseX
# container's versions:
#
VOLUME ["/repo", "/webapp"]

#
# End of Dockerfile
#


