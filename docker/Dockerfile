# 使用Node.js官方镜像作为基础镜像
FROM node:16

# 设置工作目录
WORKDIR /app

# 克隆存储库
RUN git clone --depth=1 https://github.com/ZanderZhao/zmind-backend.git .  && \
    apt-get update -y && \
    apt-get upgrade -y && \
    npm install && \
    npm run build && \
    apt-get clean && \
    npm cache clean --force && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/apk/* && \
    rm -rf /root/.npm /root/.node-gyp /root/.gnupg /usr/share/man /tmp/*
    
    # sed -i 's/module\.exports = {/module.exports = {devServer: { disableHostCheck: true },/' vue.config.js  && \
    # npm install --legacy-peer-deps && \

# 暴露服务的端口
EXPOSE 8080
# 启动服务
CMD [ "npm", "run", "serve" ]

# 清理缓存
# RUN apt-get clean && \
#     npm cache clean --force && \
#     rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/apk/* && \
#     rm -rf /root/.npm /root/.node-gyp /root/.gnupg /usr/share/man /tmp/*

# docker build -t zmind-backend .
# docker run -p 4000:8080 zmind-backend
# docker login
# docker images
# docker tag zmind-backend:latest zanderzhao/zmind-backend:v0.0.2
# docker push zanderzhao/zmind-backend:v0.0.2
# echo -n mypw. | docker login --username zanderzhao --password-stdin