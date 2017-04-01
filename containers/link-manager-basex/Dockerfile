FROM basex/dba
MAINTAINER Eliot Kimber "ekimber@contrext.com"

# ENV HOME /opt/basex
# ENV PATH $HOME/bin:$PATH
ENV WEBAPPDIR /srv/BaseXWeb
ENV REPODIR /srv/BaseXRepo

USER root

#
# Get the Link Manager web application source:
#

RUN wget -O /tmp/develop.zip https://github.com/dita-for-small-teams/d4st-linkmgmt-basex/archive/develop.zip && \
    unzip /tmp/develop.zip -d /tmp && \    
    rm /tmp/develop.zip && \     
    cp /tmp/d4st-linkmgmt-basex-develop/webapp/*.xqm ${WEBAPPDIR}/  && \    
    cp -r /tmp/d4st-linkmgmt-basex-develop/webapp/static/* ${WEBAPPDIR}/static/  && \ 
    cp -r /tmp/d4st-linkmgmt-basex-develop/modules/* ${REPODIR}  && \  
    mkdir -p ${WEBAPPDIR}/dba/modules/modules && \  
    cp /tmp/d4st-linkmgmt-basex-develop/modules/dba/*.xqm ${WEBAPPDIR}/dba/modules/ && \  
    cp /tmp/d4st-linkmgmt-basex-develop/modules/dba/*.xqm ${WEBAPPDIR}/dba/modules/modules/
      
COPY basex/dot_basex  /srv/.basex 
RUN chown basex /srv/.basex && \
    ls -al /srv
#RUN echo "/srv/.basex:"
#RUN cat /srv/.basex

# Get the BaseX Ruby client and add it to the bin/ directory so we have it handy 
# if we need it (but note that the GitLab container also gets its own copy of this
# file and stores it with the post-receive git hook there).
#RUN wget -O ${HOME}/bin/BaseXClient.rb https://github.com/BaseXdb/basex/raw/master/basex-api/src/main/ruby/BaseXClient.rb && \
#  chmod a+x ${HOME}/bin/*.rb && \
#  ls -al bin

# ports are defined basex/basexhttp base container.

USER basex

# Specify -d to start in the background:
# ENTRYPOINT ["/opt/basex/bin/basexhttp", "-d"]

#
# End of Dockerfile
#