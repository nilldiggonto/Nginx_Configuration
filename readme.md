#### DEBIAN BASED SYSTEM

* Installing Nginx
    ```
    $ apt-get update
    $ apt-get install nginx
    $ systemct enable nginx
    $ systemct restart nginx
    $ systemctl status nginx (Check if nginx is running) 
    $ ps aux | nginx
    $ netstat -ltnp | grep :80
    ```

* nginx command
    ```
    $ nginx -h (help command)
    $ nginx -s stop (stop the service-terminated)
    ```

* Adding to systemd Manually
    ```
    $ cd /etc/systemd/system
    $ vim nginx.service
        [Unit]
        Description=The NGINX HTTP and reverse proxy server
        After=syslog.target network-online.target remote-fs.target nss-lookup.target
        Wants=network-online.target

        [Service]
        Type=forking
        PIDFile=/run/nginx.pid
        ExecStartPre=/usr/sbin/nginx -t
        ExecStart=/usr/sbin/nginx
        ExecReload=/usr/sbin/nginx -s reload
        ExecStop=/bin/kill -s QUIT $MAINPID
        PrivateTmp=true

        [Install]
        WantedBy=multi-user.target

    ```

* nginx.conf
    ```
    //context /scope

        location {}

    //directive
        server_name google.com
        //Standard Directive

        //Array Directive
        * Access log
        * Error log        

        //Action Directive
    ```

* Nginx Process
    ```
    $ systemctl status nginx
    $ nproc (to know how many core i have)
    $ lscpu (Details of my core)
    // Master Process

    // Worker Process
        $ ulimit -n (max )
        nginx.conf: event { worker_connections 1000}
    ```
* Nginx Cache
    ```
    server {
        location ~* \.(css|js|jpg|png|mp4)$ {
            access_log off;
            add_header Cache-Control public;
            add_header Pagma public;
            add_header Vary Accept-Encoding;
            expires 1h;
        }
    }
    ```



