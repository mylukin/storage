# ================= elasticsearch =================
FROM elasticsearch:8.15.2 as es

# Define working directory.
WORKDIR /usr/share/elasticsearch
# 覆盖 jvm.options 
# COPY ./jvm.options /usr/share/elasticsearch/config/jvm.options
# 安装IK插件
RUN yes | ./bin/elasticsearch-plugin install \
  https://get.infini.cloud/elasticsearch/analysis-ik/8.15.2

VOLUME [ "/usr/share/elasticsearch/data" ]