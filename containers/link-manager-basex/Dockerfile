FROM dfst/basex:latest
MAINTAINER Eliot Kimber "ekimber@contrext.com"
# The directory structure of the container
# is /home/basex, so everything we want
# to add goes inside the basex/ directory
#
# The base container sets the working directory
# to /home/basex
#
# Add the DFST link manager web app from
# github:
RUN wget https://github.com/dita-for-small-teams/dfst-linkmgmt-basex/archive/develop.zip
RUN unzip develop.zip 
RUN cp dfst-linkmgmt-basex-develop/webapp/*.xqm basex/webapp/
RUN cp -r dfst-linkmgmt-basex-develop/webapp/static/* basex/webapp/static/
RUN cp -r dfst-linkmgmt-basex-develop/modules/* basex/repo
# Get rid of unwanted file. This is a hack but easier
# than figuring out how to exclude from Zip extraction
# or modifying the github project for now.
RUN rm basex/webapp/dita-utils-test-ui.xqm
CMD basex/bin/basexhttp -h 8984

