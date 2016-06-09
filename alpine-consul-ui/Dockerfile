FROM smebberson/alpine-consul:2.0.0
MAINTAINER Scott Mebberson <scott@scottmebberson.com>

ENV CONSUL_VERSION=0.6.4

# Download and install Consul UI
RUN apk add --update curl && \
    mkdir -p /tmp/dist && \
    curl -sSL -o /tmp/dist/consul_web_ui.zip https://releases.hashicorp.com/consul/{$CONSUL_VERSION}/consul_{$CONSUL_VERSION}_web_ui.zip && \
    cd /tmp/dist && \
    unzip consul_web_ui.zip && \
    rm -rf consul_web_ui.zip && \
    mkdir /ui && \
    mv * /ui && \
    chown -R consul:consul /ui && \
    apk del --purge curl && \
    rm -rf /var/cache/apk/* tmp/dist/consul_web_ui.zip

# Add the files
ADD root /

# Expose the web ui port
EXPOSE 8500
