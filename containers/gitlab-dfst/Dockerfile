FROM gitlab/gitlab-ce
# Copied from the base GitLab Docker file
# (https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/docker/Dockerfile):
# Wrapper to handle signal, trigger runit and reconfigure GitLab
#
# Set up configuration scripts and
# custom hooks
#
COPY admin-scripts /var/opt/dfst/bin/
RUN apt-get install -y unzip && \
    cd /var/opt/dfst/bin && \
    chmod a+x *
RUN cd /var/opt/dfst && \
    wget https://github.com/dita-for-small-teams/dfst-git-commit-hooks/archive/develop.zip && \
    unzip develop.zip && \
    rm develop.zip && \
    mv dfst-git-commit-hooks-develop/server-side custom_hooks     

ENV PATH ${PATH}:/var/opt/dfst/bin

CMD ["/assets/wrapper"]
#
# End of Docker file
#
