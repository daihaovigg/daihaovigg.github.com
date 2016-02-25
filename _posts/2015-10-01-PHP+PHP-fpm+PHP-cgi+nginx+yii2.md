打开nginx，再打开php-fpm，然后配置nginx.conf：

	location / {
            root   /home/dai/myPHP;
            index  index.html index.htm index.php;
        }
        
    location ~ \.php$ {
            root           html;
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  /home/dai/myPHP/$fastcgi_script_name;
            include        fastcgi_params;
        }
同时，为保证js和css被引用，在nginx.conf中加入：
	
	user root;
以保证nginx的用户有权限读取web目录。

然后执行php-cgi -b 9000，php运行。