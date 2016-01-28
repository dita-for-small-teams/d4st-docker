FROM java:8
ENV BASEX_VERSION 8.3
ENV BASEX_VERSION_NODOT 83
# Make the data, repo, and webapp directories available
# as volumes. 
# 
# In particular this allows the data directory to be stored
# directly on the host machine so that the link management
# database is not lost if the container is deleted.
RUN mkdir -p /opt/basex/data && \
    mkdir -p /opt/basex/repo && \
    mkdir -p /opt/basex/webapp
RUN chmod -R a+rwx /opt 

# Set up Basex user
RUN useradd -u 5555 -ms /bin/bash basex
ENV HOME /home/basex
USER 5555
WORKDIR /home/basex

RUN wget -O basex.zip http://files.basex.org/releases/${BASEX_VERSION}/BaseX${BASEX_VERSION_NODOT}.zip
RUN unzip basex.zip
# Link the default directories to the mounts in 
# /opt/basex so the mounts are in a consistent
# location.
RUN cp -r /home/basex/basex/webapp /opt/basex
RUN rm -Rf /home/basex/basex/data && \
    rm -Rf /home/basex/basex/repo  && \
    rm -Rf /home/basex/basex/webapp
RUN ln -s /opt/basex/data /home/basex/basex  && \
    ln -s /opt/basex/repo /home/basex/basex  && \
    ln -s /opt/basex/webapp /home/basex/basex 

# Expose the ports for the base BaseX server (used by the DFST git commit hooks
# and the HTTP server, respectively:
EXPOSE 1984 8984
# Make it easy to run the basex client:
ENV PATH /home/basex/bin:$PATH
CMD basex/bin/basexhttp -h 8984