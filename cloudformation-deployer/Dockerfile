# This file is automatically generated by the Nebula SDK. DO NOT EDIT.

FROM python:3-alpine
RUN set -eux ; \
    mkdir -p /tmp/ni && \
    cd /tmp/ni && \
    wget https://packages.nebula.puppet.net/sdk/ni/v1/ni-v1-linux-amd64.tar.xz && \
    wget https://packages.nebula.puppet.net/sdk/ni/v1/ni-v1-linux-amd64.tar.xz.sha256 && \
    echo "$( cat ni-v1-linux-amd64.tar.xz.sha256 )  ni-v1-linux-amd64.tar.xz" | sha256sum -c - && \
    tar -xvJf ni-v1-linux-amd64.tar.xz && \
    mv ni-v1*-linux-amd64 /usr/local/bin/ni && \
    cd - && \
    rm -fr /tmp/ni
RUN apk --no-cache add bash ca-certificates curl git jq openssh && update-ca-certificates
RUN ["/bin/bash", "-c", "pip install awscli"]
COPY "./step.sh" "/nebula/step-cloudformation-deployer.sh"
CMD ["/bin/bash", "/nebula/step-cloudformation-deployer.sh"]

LABEL "org.opencontainers.image.title"="AWS CloudFormation deployer"
LABEL "org.opencontainers.image.description"="The AWS CloudFormation deployer task creates or updates a CloudFormation stack using a provided template."
LABEL "com.puppet.nebula.sdk.version"="v1"
