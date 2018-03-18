ARG BUILD_FROM=hassioaddons/debian-base-amd64:1.0.0
FROM ${BUILD_FROM}

# Setup base system
RUN \
    echo 'deb http://deb.debian.org/debian jessie main' >> /etc/apt/sources.list \
    \
    && apt-get update \
    \
    && apt-get install -y --no-install-recommends libssl1.0.0 \
    \
    && rm -f -r \
        /tmp/* \
        /var/lib/apt/lists/*

# Copy root filesystem
COPY rootfs /

# Add airsonos binary
ARG BUILD_ARCH
ADD bin/airsonos-${BUILD_ARCH} /usr/bin/airsonos

# Build arugments
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="AirSonos" \
    io.hass.description="AirPlay capabilities for your Sonos (and UPnP) devices" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Franck Nijhof <frenck@addons.community>" \
    org.label-schema.description="AirPlay capabilities for your Sonos (and UPnP) devices" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="AirSonos" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://community.home-assistant.io/t/community-hass-io-add-on-airsonos/36796?u=frenck" \
    org.label-schema.usage="https://github.com/hassio-addons/addon-airsonos/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/hassio-addons/addon-airsonos" \
    org.label-schema.vendor="Community Hass.io Add-ons"
