#stole from svendowideit/samba, with workaround for docker 1.11.1 and later
FROM		debian:stable
LABEL		CMDBUILD="docker build -t njhsi/samba https://raw.githubusercontent.com/njhsi/dockerfiles/master/samba/Dockerfile"
LABEL		CMDRUN="docker run njhsi/samba"

MAINTAINER	njhsi

# gettext for envsubst
RUN		apt-get update && \
			apt-get install -yq samba gettext
ADD		share.tmpl /share.tmpl
ADD		setup.sh /setup.sh

#njshi: aded below sed lines to workaroud for docker 1.11.1+
RUN sed --in-place 's/USER=/export USER=/g' /setup.sh
RUN sed --in-place 's/PASSWORD=/export PASSWORD=/g' /setup.sh
RUN sed --in-place 's/USERID=/export USERID=/g' /setup.sh
RUN sed --in-place 's/GROUP=/export GROUP=/g' /setup.sh
RUN sed --in-place 's/DOCKER_HOST=/export DOCKER_HOST=/g' /setup.sh
RUN sed --in-place 's/READONLY=/export READONLY=/g' /setup.sh
RUN sed --in-place 's/CONTAINER=/export CONTAINER=/g' /setup.sh
RUN sed --in-place 's/Init Path/Root Dir/g' /setup.sh
RUN chmod +x /setup.sh

ENTRYPOINT      ["/setup.sh"]
