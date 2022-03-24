#### DEBIAN BASED SYSTEM

* Installing Nginx
    ```
    $ apt-get update
    $ apt-get install nginx
    $ systemctl status nginx (Check if nginx is running)
    $ ps aux | nginx
    $ netstat -ltnp | grep :80
    ```