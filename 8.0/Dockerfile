FROM bitnami/minideb-extras:jessie-r14
MAINTAINER Bitnami <containers@bitnami.com>

ENV BITNAMI_APP_NAME="tomcat" \
    BITNAMI_IMAGE_VERSION="8.0.43-r1" \
    JAVA_OPTS="-Djava.awt.headless=true -XX:+UseG1GC -Dfile.encoding=UTF-8" \
    PATH="/opt/bitnami/java/bin:/opt/bitnami/tomcat/bin:$PATH" \
    TOMCAT_AJP_PORT="8009" \
    TOMCAT_ALLOW_REMOTE_MANAGEMENT="0" \
    TOMCAT_HTTP_PORT="8080" \
    TOMCAT_SHUTDOWN_PORT="8005" \
    TOMCAT_USERNAME="user"

# Install required system packages and dependencies
RUN install_packages libc6 libexpat1 libffi6 libfontconfig1 libfreetype6 libgcc1 libglib2.0-0 liblzma5 libpcre3 libpng12-0 libselinux1 libstdc++6 libx11-6 libxau6 libxcb1 libxdmcp6 libxext6 libxml2 zlib1g
RUN bitnami-pkg install java-1.8.0_121-0 --checksum 2743f753fd1ea88bf90352d95694f89ab0a0fb855cf0d1c7b2a6d92835f9ad27
RUN bitnami-pkg unpack tomcat-8.0.43-0 --checksum c645aef1669738222df7c2f9a0350467896c4a0ee49c7d67193981de9ab36f1f
RUN ln -sf /opt/bitnami/tomcat/data /app

COPY rootfs /

VOLUME ["/bitnami/tomcat"]

EXPOSE 8080

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","tomcat"]
