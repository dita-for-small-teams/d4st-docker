FROM java:8
RUN useradd -u 5555 -ms /bin/bash basex

ENV HOME /home/basex
USER 5555 
WORKDIR /home/basex

RUN wget -O basex.zip http://files.basex.org/releases/8.3/BaseX83.zip
RUN unzip basex.zip
EXPOSE 8984 8984 
EXPOSE 1984 1984
CMD basex/bin/basexhttp
