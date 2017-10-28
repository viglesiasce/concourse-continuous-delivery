FROM concourse/git-resource

ENV PATH=$PATH:/usr/local/google-cloud-sdk/bin
ENV GCLOUD_SDK_VERSION=177.0.0
ENV GCLOUD_SDK_URL=https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-${GCLOUD_SDK_VERSION}-linux-x86_64.tar.gz

# Install gcloud
RUN apk update && apk add curl openssl python \
 && mkdir -p /usr/local && cd /usr/local \
 && wget -q -O - $GCLOUD_SDK_URL |tar zxf - \
 && /bin/bash -l -c "echo Y | /usr/local/google-cloud-sdk/install.sh && exit"