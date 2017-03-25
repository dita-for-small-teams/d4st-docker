FROM java:8
MAINTAINER Eliot Kimber "ekimber@contrext.com"

ENV HOME /opt/basex
ENV PATH $HOME/bin:$PATH

# Define working directory.
WORKDIR /opt/basex

#
# Get the Link Manager web application source:
#

RUN wget https://github.com/dita-for-small-teams/dfst-linkmgmt-basex/archive/develop.zip && \
  unzip develop.zip && \
  rm develop.zip

RUN apt-get install unzip && \
  wget -O /tmp/BaseX.zip http://files.basex.org/releases/BaseX-latest.zip && \ 
  unzip /tmp/BaseX.zip -d /opt/ && \
  rm /tmp/BaseX.zip && \
  mv /opt/basex/data / && \
  mv /opt/basex/repo / && \
  mv /opt/basex/webapp / && \
  cp dfst-linkmgmt-basex-develop/webapp/*.xqm /webapp/ && \
  cp -r dfst-linkmgmt-basex-develop/webapp/static/* /webapp/static/ && \
  cp -r dfst-linkmgmt-basex-develop/modules/dba /webapp/dba/modules && \
  cp -r dfst-linkmgmt-basex-develop/modules/* /repo

    

# Get the BaseX Ruby client and add it to the bin/ directory so we have it handy 
# if we need it (but note that the GitLab container also gets its own copy of this
# file and stores it with the post-receive git hook there).
RUN wget -O bin/BaseXClient.rb https://github.com/BaseXdb/basex/raw/master/basex-api/src/main/ruby/BaseXClient.rb && \
  chmod a+x bin/*.rb && \
  ls -al bin

COPY basex/dot_basex /opt/basex/dot_basex

RUN cat /opt/basex/dot_basex >> .basex && rm /opt/basex/dot_basex
# Expose port.

EXPOSE 8984
EXPOSE 1984

#
# Define the volumes used by the server:
#

VOLUME ["/data"]

# Define default command.
ENTRYPOINT ["/opt/basex/bin/basexhttp", "-d"]

#
# End of Dockerfile
#