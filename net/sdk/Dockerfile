FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine

LABEL mantainer "Innovabit S.A.C."

RUN apk update \
    && apk add --update curl gnupg \
    && apk add --update nodejs \
    && apk add --update npm \
    && apk add --update git

RUN dotnet nuget locals all -c