FROM suse/sles12:latest
MAINTAINER Crisdorz <cledorze@suse.com>
ADD http://sle11sp3-1.dorz.fr/smt.crt /etc/pki/trust/anchors/smt.crt
RUN update-ca-certificates
RUN zypper ref -s
#RUN zypper ar http://sle11sp3-1.dorz.fr/repo/SUSE/Products/SLE-Module-Web-Scripting/12/x86_64/ SLE12-WS
#RUN zypper ar http://sle11sp3-1.dorz.fr/repo/SUSE/Products/SLE-Module-Containers/12/x86_64/ SLE12-DK
RUN zypper lr

ENV MYSQL_USER=admin \
    MYSQL_PASS=mage \
    MYSQL_ROOT_PASSWORD=mage \
    MYSQL_USER=mage \
    MYSQL_PASSWORD=mage \
    MYSQL_DATABASE=mage	\
    ON_CREATE_DB=mage \
    REPLICATION_MASTER=replica \
    REPLICATION_SLAVE=replica \
    REPLICATION_USER=replica \
    REPLICATION_PASS=replica

RUN zypper -n in net-tools mariadb
RUN mkdir -p /var/log/mysql 
RUN mysql_install_db > /dev/null 2>&1 && touch /var/lib/mysql/.EMPTY_DB 
RUN chown -R mysql:mysql /var/lib/mysql
# expose database port
EXPOSE 3306

# remember that mysql still has
# to be configured before
# this next command will work

CMD ["/usr/bin/mysqld_safe"]


