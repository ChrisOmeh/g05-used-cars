FROM python:3.7-stretch

# Downloading gcloud package
RUN curl https://dl.google.com/dl/cloudsdk/release/google-cloud-sdk.tar.gz > /tmp/google-cloud-sdk.tar.gz

# Installing the package
RUN mkdir -p /usr/local/gcloud \
    && tar -C /usr/local/gcloud -xvf /tmp/google-cloud-sdk.tar.gz \
    && /usr/local/gcloud/google-cloud-sdk/install.sh

# Adding the package path to local
ENV PATH $PATH:/usr/local/gcloud/google-cloud-sdk/bin
ENV GOOGLE_APPLICATION_CREDENTIALS=hamoye-296618-8e48c5c60c4f.json

WORKDIR /opt
ADD requirements.txt .
RUN pip install -r requirements.txt

ADD . .

ENTRYPOINT [ "python" ]
CMD ["model.py"]