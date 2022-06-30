FROM alpine:3.10

# Update
RUN apk --update add --no-cache bash nodejs-current yarn curl busybox-extras vim rsync git mysql-client openssh-client 
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.18.0/bin/linux/amd64/kubectl && chmod +x ./kubectl && mv ./kubectl /usr/local/bin/kubectl

# Scripts
RUN mkdir /srv/jobs
COPY jobs/* /srv/jobs/

# Backup Folder
RUN mkdir /var/backup
RUN mkdir /var/backup/mysql