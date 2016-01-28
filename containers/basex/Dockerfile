FROM java:8
# Make the data, repo, and webapp directories available
# as volumes. 
# 
# In particular this allows the data directory to be stored
# directly on the host machine so that the link management
# database is not lost if the container is deleted.
RUN mkdir -p /opt/basex
RUN chmod -R a+rwx /opt 
RUN ln -s /home/basex/basex/data /opt/basex/data && \
    ln -s /home/basex/basex/repo /opt/basex/repo && \
    ln -s /home/basex/basex/webapp /opt/basex/webapp

# Set up Basex user
RUN useradd -u 5555 -ms /bin/bash basex
ENV HOME /home/basex
USER 5555
WORKDIR /home/basex

RUN wget -O basex.zip http://files.basex.org/releases/8.3/BaseX83.zip
RUN unzip basex.zip
# Expose the ports for the base BaseX server (used by the DFST git commit hooks
# and the HTTP server, respectively:
EXPOSE 1984 8984
# Make it easy to run the basex client:
ENV PATH /home/basex/bin:$PATH
CMD basex/bin/basexhttp -h 8984