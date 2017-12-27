=======
Docs build using http://www.sphinx-doc.org

== nginx config

```

http {
    include       mime.types;
    default_type  application/octet-stream;


    sendfile        on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;
	
	server {
	  listen                    80;
	  server_name               localhost;
	  server_tokens             off;
	  root                      /dev/null;

	  # Increase this if you want to upload larger attachments
	  client_max_body_size      20m;

	  # individual nginx logs for this vhost
	  access_log                ./logs/delven_access.log;
	  error_log                 ./logs/delven_error.log;
  
  # angular 
	 location / {
		proxy_read_timeout      1;
		proxy_connect_timeout   1;
		#proxy_redirect          off;

		proxy_set_header        X-Forwarded-Proto $scheme;
		proxy_set_header        Host              $http_host;
		proxy_set_header        X-Real-IP         $remote_addr;
		proxy_set_header        X-Forwarded-For   $proxy_add_x_forwarded_for;
		proxy_set_header        X-Frame-Options   SAMEORIGIN;

		proxy_pass              http://localhost:4200/;
	  }
	 
    # websockets for angular	 
	location /sockjs-node {
	     proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        rewrite ^/(.*)$  /$1  break;
        proxy_set_header Host localhost;
        proxy_pass http://localhost:4200/;	
	  }
	  
	 # API Server (spring-boot)
   
   	 location /api {
	    # Allow for debuging
		proxy_read_timeout      360;
		proxy_connect_timeout   360;
		#proxy_redirect          off;

		proxy_set_header        X-Forwarded-Proto $scheme;
		proxy_set_header        Host              $http_host;
		proxy_set_header        X-Real-IP         $remote_addr;
		proxy_set_header        X-Forwarded-For   $proxy_add_x_forwarded_for;
		proxy_set_header        X-Frame-Options   SAMEORIGIN;

		proxy_pass              http://localhost:8877/;
	  }
	  
	}
}
```


