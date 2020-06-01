FROM opensciencegrid/xcache:fresh

LABEL maintainer OSG Software <help@opensciencegrid.org>

RUN yum install -y --enablerepo=osg-testing --enablerepo=osg-contrib \
               atlas-xcache \
               xcache-consistency-check && \
    yum clean all --enablerepo=* && rm -rf /var/cache/

COPY update-agis-status.sh /usr/local/sbin/
COPY 10-atlas-xcache-limits.conf /etc/security/limits.d
COPY supervisord.d/10-atlas-xcache.conf /etc/supervisord.d/
COPY image-config.d/* /etc/osg/image-config.d/
COPY cron.d/* /etc/cron.d/
COPY xcache-consistency-check-wrapper.sh /usr/bin/xcache-consistency-check-wrapper.sh
