
---------------------------------------------------------------------------------------------------------------------------------------------------------------
# docker file using amazoncorrentto as base image which contain java 11 


# FROM amazoncorretto:11
# RUN curl https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar -o spring-petclinic-2.4.2.jar
# EXPOSE 8080
# CMD [ "java" , "-jar", "spring-petclinic-2.4.2.jar" ]
# LABEL  Author="sangamesh" 


# modifying above file with add instructions

# FROM amazoncorretto:11
# LABEL  Author="sangamesh" 
# ADD https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar  /spring-petclinic-2.4.2.jar
# EXPOSE 8080
# CMD [ "java" , "-jar", "spring-petclinic-2.4.2.jar" ]


---------------------------------------------------------------------------------------------------------------------------------------------------------------

#docker file fot dotnet application 

# FROM mcr.microsoft.com/dotnet/sdk:7.0
# LABEL Owner="sangamesh"
# ARG DOWNLOAD_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip
# ARG HOME_DIR=/nop
# ARG user=nopcommerce
# ARG group=nopcommerce
# ARG uid=1000
# ARG gid=1000


# RUN apt update  && apt install unzip -y
# RUN groupadd -g ${gid} ${group} \
#     && useradd -d ${HOME_DIR} -u ${uid} -g ${gid} -m -s /bin/bash ${user}
# USER ${user}
# WORKDIR ${HOME_DIR}
# ADD  --chown=${user}:${group} ${DOWNLOAD_URL} ${HOME_DIR}/nopCommerce_4.60.2_NoSource_linux_x64.zip

#  RUN unzip ${HOME_DIR}/nopCommerce_4.60.2_NoSource_linux_x64.zip && \
#     mkdir ${HOME_DIR}/logs && mkdir ${HOME_DIR}/bin


# EXPOSE 5000
# ENV ASPNETCORE_URLS="http://0.0.0.0:5000"
# CMD [ "dotnet" , "Nop.Web.dll" ]
---------------------------------------------------------------------------------------------------------------------------------------------------------------
# docker file using alpine as base image

# FROM alpine:3
# RUN apk add openjdk11
# RUN wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar
# EXPOSE 8080
# CMD ["java", "-jar", "spring-petclinic-2.4.2.jar"]


---------------------------------------------------------------------------------------------------------------------------------------------------------------



# multi stage docker file spring petclinic 
------------------------------------------

# FROM ubuntu:22.04 AS extractor
# RUN apt update && apt install unzip
# ARG DOWNLOAD_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip
# ADD ${DOWNLOAD_URL} /nopCommerce/nopCommerce_4.60.2_NoSource_linux_x64.zip
# RUN cd /nopCommerce && unzip nopCommerce_4.60.2_NoSource_linux_x64.zip && mkdir bin logs && rm nopCommerce_4.60.2_NoSource_linux_x64.zip


# FROM mcr.microsoft.com/dotnet/sdk:7.0
# LABEL author="khaja" organization="qt" project="learning"
# ARG user=nopcommerce
# ARG group=nopcommerce
# ARG uid=1000
# ARG gid=1000
# ARG DOWNLOAD_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip
# ARG HOME_DIR=/nop
# RUN apt update && apt install unzip -y
# # Create user nopcommerce
# RUN groupadd -g ${gid} ${group} \
#     && useradd -d "$HOME_DIR" -u ${uid} -g ${gid} -m -s /bin/bash ${user}
# USER ${user}
# WORKDIR ${HOME_DIR}
# COPY --from=extractor  /nopCommerce ${HOME_DIR}
# EXPOSE 5000
# ENV ASPNETCORE_URLS="http://0.0.0.0:5000"
# CMD [ "dotnet", "Nop.Web.dll"]



# multi stage docker file game of life 
--------------------------------------

# FROM alpine/git AS vcs
# RUN cd / && git clone https://github.com/spring-projects/spring-petclinic.git && \
#     pwd && ls /spring-petclinic

# FROM maven:3-amazoncorretto-17 AS builder
# COPY --from=vcs /spring-petclinic /spring-petclinic
# RUN ls /spring-petclinic 
# RUN cd /spring-petclinic && mvn package



# FROM amazoncorretto:17-alpine-jdk
# LABEL author="khaja"
# EXPOSE 8080
# ARG HOME_DIR=/spc
# WORKDIR ${HOME_DIR}
# COPY --from=builder /spring-petclinic/target/spring-*.jar ${HOME_DIR}/spring-petclinic.jar
# EXPOSE 8080
# CMD ["java", "-jar", "spring-petclinic.jar"]


---------------------------------------------------------------------------------------------------------------------------------------------------------------
