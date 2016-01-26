FROM java:8
RUN useradd -u 5555 -ms /bin/bash basex

ENV HOME /home/basex
USER 5555
WORKDIR /home/basex

RUN wget -O basex.zip http://files.basex.org/releases/8.3/BaseX83.zip
RUN unzip basex.zip
# Expose the ports for the base BaseX server (used by the DFST git commit hooks
# and the HTTP server, respectively:
EXPOSE 1984 8984
CMD basex/bin/basexhttp -h 8984