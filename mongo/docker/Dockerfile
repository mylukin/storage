# ================= mongo-rsinit =================
FROM mongo:7 as mongo
ADD ./mongo.key /mongo.key
RUN chown mongodb:mongodb /mongo.key && chmod 400 /mongo.key