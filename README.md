# php_Error_anomaly
php的错误处理，异常处理


     错误处理
     
           	1. 语法错误
           
          	2. 运行时的错误
           
          	3. 逻辑错误
           
          	
           	错误报告：
           
          		错误 E_ERROR
           
          		警告 E_WARNING
           
          		注意 E_NOTICE
              
           	开发阶段：开发时输出所有的错误报告，有利于我们进行程序调试
           	运行阶段：不要让程序输出任何一种错误报告（不能让用户看到（懂技术， 不懂技术））
           
           	将错误报告写入日志中
           		一、指定错误报告 error_reporting = E_LL
           		二、关闭错误输出 display_errors = Off
           		三、开启错误日志功能 log_errors = On
           
           		1. 默认如果不指定错误日志位置，则默认写WEB服务器的日志中
            	2. 为error_log选项指定 一个文件名（可写）
           		3. 写入到操作系统日志中error_log=syslog
           
              异常处理
            error_reporting   设置应该报告何种 PHP 错误
            ini_set   为一个配置选项设置值
            ini_get   获取一个配置选项的值
            error_log  发送错误信息到某个地方
            
            
            
          	error_reporting(E_ALL);  

          	ini_set("display_errors", "off");  （这里把所有错误报告关闭）

          	ini_set("error_log", "syslog");    这里意思把错误报告文件放在电脑系统里
          	ini_set("MAX_FILEUPLOAD", 200000000);   

          	echo ini_get("upload_max_filesize");

          	error_log("this is a error message!!!!");


            getType($var);   //注意

            getType();  //警告

            getTye();  //错误  会终止程序运行

            echo "###########################<br>";

 	







