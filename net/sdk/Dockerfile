FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine

LABEL mantainer "Innovabit S.A.C."

RUN apk update \
    && apk add --update curl gnupg \
    && apk add --update nodejs \
    && apk add --update npm \
    && apk add --update 'libretls<3.3.3p1-r3' \
    && apk add --update 'krb5-libs<1.18.5-r0'

RUN dotnet nuget locals all -c

RUN dotnet tool install -g dotnet-reportgenerator-globaltool