FROM openjdk:21-jdk-slim

# 设置维护者信息
LABEL maintainer="hsyuan@nchu.cn"
LABEL version="0.0.1"

# 设置环境
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8


# 设置时区
RUN apt-get update && \
    apt-get install -y tzdata && \
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo 'Asia/Shanghai' > /etc/timezone && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /inventropy
WORKDIR /inventropy

# 通过构建参数指定 jar 文件路径
ARG JAR_FILE=inventropy.jar
COPY ${JAR_FILE} /inventropy/inventropy.jar

ENTRYPOINT ["java", "-jar", "/inventropy/inventropy.jar"]

EXPOSE 8080