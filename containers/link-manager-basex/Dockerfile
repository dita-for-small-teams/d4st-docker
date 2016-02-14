FROM basex/basexhttp:latest
MAINTAINER Eliot Kimber "ekimber@contrext.com"
#
# The basex/basexhttp setup puts the data, repo.
# and webapp directories at the root of the file system
#
# The base container sets the working directory
# to /opt/basex
#
# Add the DFST link manager web app from
# github:
RUN wget https://github.com/dita-for-small-teams/dfst-linkmgmt-basex/archive/develop.zip && \
  unzip develop.zip && \
  rm develop.zip
RUN wget -O bin/BaseXClient.rb https://github.com/BaseXdb/basex/raw/master/basex-api/src/main/ruby/BaseXClient.rb && \
  chmod a+x bin/*.rb && \
  ls -al bin

RUN cp dfst-linkmgmt-basex-develop/webapp/*.xqm /webapp/ && \
    cp -r dfst-linkmgmt-basex-develop/webapp/static/* /webapp/static/ && \
    cp -r dfst-linkmgmt-basex-develop/modules/* /repo
COPY basex/dot_basex /opt/basex

RUN cat /opt/basex/dot_basex >> .basex && rm /opt/basex/dot_basex
#
# Make the basex executables available to other containers:
#
VOLUME /opt/basex/bin
#
# End of Dockerfile
#


