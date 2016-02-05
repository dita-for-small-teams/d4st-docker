Base DITA OT Container
================================

This image provides a base DITA Open Toolkit
image that can be used as the base for other
Open Toolkit images that reflect specific plugins
or additional Ant scripts or whatever.

Images intended to be used should declare volumes
using these VOLUME instructions, as used in the
dfst/dita-ot image:

~~~~
VOLUME /opt/dita-ot/DITA-OT
VOLUME /opt/dita-ot/userdata
~~~~
 