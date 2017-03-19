# GitLab image configured for use in the DITA for Small Teams
# system. Adds custom git hooks to the base image.
#
# Using the sameersbn version because it's better documented
# and generally better organized than the office gitlab-ce 
# container.
FROM sameersbn/gitlab:8.17.3
MAINTAINER Eliot Kimber "ekimber@contrext.com"
COPY admin-scripts /var/opt/dfst/bin/
RUN cd /var/opt/dfst && \
    wget https://github.com/dita-for-small-teams/dfst-git-commit-hooks/archive/develop.zip && \
    unzip develop.zip && \
    rm develop.zip && \
    mv dfst-git-commit-hooks-develop/server-side custom_hooks && \
    cd /var/opt/dfst/bin && \
    chmod a+x * 
    
ENV PATH ${PATH}:/var/opt/dfst/bin
ENTRYPOINT ["/sbin/entrypoint.sh"]
CMD ["app:start"]
#
# End of Docker file
#
