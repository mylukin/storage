# ================= elasticsearch =================
FROM elasticsearch:7.17.24 as es

# Define working directory.
WORKDIR /usr/share/elasticsearch
# 覆盖 jvm.options
# COPY ./jvm.options /usr/share/elasticsearch/config/jvm.options
# 安装IK插件
RUN yes | ./bin/elasticsearch-plugin install \
  https://get.infini.cloud/elasticsearch/analysis-ik/7.17.24

# 安装Kuromoji插件（日语分词器）
RUN yes | ./bin/elasticsearch-plugin install analysis-kuromoji

# 安装Nori插件（韩语分词器）
RUN yes | ./bin/elasticsearch-plugin install analysis-nori

VOLUME [ "/usr/share/elasticsearch/data" ]
