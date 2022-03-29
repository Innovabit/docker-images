FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine

LABEL mantainer "Innovabit S.A.C."

RUN apk update \
    && apk add --update 'libretls=3.3.3p1-r3' \
    && apk add --update 'krb5-libs=1.18.5-r0' \
    && apk add --update --no-cache tzdata
    
ENV TZ=America/New_York

ENV DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=false