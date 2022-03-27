FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine

LABEL mantainer "Innovabit S.A.C."

RUN apk update \
    && apk add --update curl gnupg \
    && apk add --update nodejs \
    && apk add --update npm \
    && apk add --update libretls/libretls \
    && apk add --update krb5/krb5-libs

RUN dotnet nuget locals all -c

RUN dotnet tool install -g dotnet-reportgenerator-globaltool