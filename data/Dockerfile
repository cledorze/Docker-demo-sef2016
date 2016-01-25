FROM suse/sles12:latest
MAINTAINER Chrisdorz <cledorze@suse.com>
ADD http://sle11sp3-1.dorz.fr/smt.crt /etc/pki/trust/anchors/smt.crt
RUN update-ca-certificates
RUN zypper ref -s
RUN zypper lr
COPY . /
COPY true-asm /bin/echo
VOLUME ["/srv/magento", "/var/lib/mysql"]
ENTRYPOINT ["/bin/echo"]
