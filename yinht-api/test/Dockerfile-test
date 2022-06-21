FROM reg.yhroot.com/yinhe-pub/python:3.8-build
## 项目根目录
ARG appname=$appname
ARG dpenv=$dpenv
ARG apphome=/yinhe/apps/$appname
ARG applog=/yinhe/logs/$appname
ARG ENV=$ENV
USER root
WORKDIR $apphome
RUN useradd -m -d $apphome -u 1000 yinhe
COPY . .
COPY apps_config /yinhe/apps/config/$appname/
RUN  mkdir -p $applog && chown -R yinhe:yinhe /yinhe  && chmod +x ./scripts/build-tool.sh && chown -R yinhe:yinhe /yinhe/apps/config/$appname/
USER root
ENV APPNAME=$appname
ENTRYPOINT ["bash", "-c", "./scripts/build-tool.sh start"] 
ARG GIT_TAG=$GIT_TAG
ARG GIT_COMMIT=$GIT_TAG
ENV GIT_TAG=$GIT_TAG
ENV GIT_COMMIT=$GIT_COMMIT
