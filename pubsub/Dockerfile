# Use a imagem base do Python como base para o ambiente de desenvolvimento
FROM gcr.io/google.com/cloudsdktool/google-cloud-cli:latest

EXPOSE 8085

RUN apt-get -f install google-cloud-sdk-pubsub-emulator google-cloud-sdk 

RUN gcloud components install pubsub-emulator \
    && gcloud components update

CMD [ "gcloud", "beta", "emulators", "pubsub", "start", "--project=PUBSUB_UNIFICATOR"] 

CMD ["sleep", "10h"]