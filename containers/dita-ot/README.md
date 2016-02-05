Out of the Box DITA OT Container
================================

This container provides an image
of the DITA Open Toolkit as 
distributed by the DITA OT project.

It defines two volumes:

- /opt/dita-ot/DITA-OT is the full DITA-OT itself
- /opt/dita-ot/userdata Is intended as a mount point for a host directory the OT can write to.

NOTE: Use the image dfst/dita-ot-base as the extension base for new DITA-OT images.
This image will not work because the volume definitions in this image prevent other images
based on it from persisting anything to the OT. 