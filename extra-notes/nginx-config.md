apt-update
apt install vim
cd /etc/nginx
vim nginx.conf >>
    events {}
    https {
      server {
        location / {
          proxy_pass http://jenkins:8080/;
        }
      }
    }
nginx -s reload
