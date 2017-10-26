FROM openmicroscopy/omero-web:latest
MAINTAINER ome-devel@lists.openmicroscopy.org.uk

USER root
RUN /opt/omero/web/venv/bin/pip install 'whitenoise<4' && \
    echo "config append -- omero.web.middleware '{\"index\": 0, \"class\": \"whitenoise.middleware.WhiteNoiseMiddleware\"}'" > /opt/omero/web/config/whitenoise.omero
COPY omeroweb-settings-consolelog.patch /opt/omero/web
RUN cd /opt/omero/web/OMERO.web/lib/python/omeroweb && patch -i /opt/omero/web/omeroweb-settings-consolelog.patch
USER omero-web
