FROM node:lts-alpine

# install packages specifically related to network troubleshooting
RUN apk add --no-cache \
	-X http://dl-cdn.alpinelinux.org/alpine/edge/main \
	-X http://dl-cdn.alpinelinux.org/alpine/edge/community \
	-X http://dl-cdn.alpinelinux.org/alpine/edge/testing \
	bash \
	bind-tools \
	curl \
	fping \
	hping3 \
	iproute2 \
	iproute2-minimal \
	iproute2-ss \
	mtr \
	openssl \
	traceroute \
	&& :

# Container environment variables
ENV NPM_CONFIG_LOGLEVEL info

# Install OpenMCT
WORKDIR /opt
RUN apk add --no-cache git && \
    git clone https://github.com/nasa/openmct.git && \
    cd openmct && \
    npm install

# Run OpenMCT
WORKDIR /opt/openmct
EXPOSE 8080
ENTRYPOINT ["npm", "start", "--", "--host", "0.0.0.0"]