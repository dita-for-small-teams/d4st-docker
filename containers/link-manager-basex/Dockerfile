FROM dfst/basexhttp-base:latest
MAINTAINER Eliot Kimber "ekimber@contrext.com"
#
# The basex/basexhttp setup puts the data, repo.
# and webapp directories at the root of the file system
#
# The base container sets the working directory
# to /opt/basex
#
#
# Get the BaseX Ruby client and add it to the bin/ directory so we have it handy 
# if we need it (but note that the GitLab container also gets its own copy of this
# file and stores it with the post-receive git hook there.
RUN wget -O bin/BaseXClient.rb https://github.com/BaseXdb/basex/raw/master/basex-api/src/main/ruby/BaseXClient.rb && \
  chmod a+x bin/*.rb && \
  ls -al bin

COPY basex/dot_basex /opt/basex/dot_basex

RUN cat /opt/basex/dot_basex >> .basex && rm /opt/basex/dot_basex
#
# Define the volumes used by the server and make
# the executables available to other containers (e.g.,
# so they can run the basexhttp clients):
#

VOLUME ["/opt/basex/bin", "/data", "/repo", "/webapp"]
#
# End of Dockerfile
#


