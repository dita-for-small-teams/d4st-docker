FROM dfst/dita-ot-base
#
# Sets up a DITA-OT container
# with all of the DITA Community 
# open toolkit plugins integrated.
#
# Sample fetch from Git:
#
# RUN wget ${DITA_COMM_URL}org.dita-community.media-d.html/archive/${BRANCH}.zip && unzip ${BRANCH}.zip -d ${DITA_HOME}/plugins && rm ${BRANCH}.zip
#
# Integrate new plugins
#
RUN ant -f integrator.xml
#
# End of Dockerfile
#

