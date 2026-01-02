FROM nginx:alpine

COPY html/ /usr/share/nginx/html/

CMD ["sh", "-c", "\
mkdir -p /data/web-logs && \
sed -i \"s/HOSTNAME_PLACEHOLDER/$(hostname)/g\" /usr/share/nginx/html/index.html && \
(while true; do \
  echo \"$(date -Iseconds) POD=$(hostname) STATUS=RUNNING\" >> /data/web-logs/run.log; \
  sleep 10; \
done) & \
nginx -g 'daemon off;' \
"]

