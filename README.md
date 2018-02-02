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

 	

异常处理


 
 
     异常处理: 意外，是在程序运行过程中发生的意料这外的事，使用异常改变脚本正常流程
 	
 	PHP5中的一个新的重要特性
 	try {
 
 	}catch(异常对象){
 
 	}
     
  	  1. 如果try中代码没有问题，则将try中代码执行完后就到catch后执行
  	  2. 如果try中代码有异常发生，则抛出一个异常对象(使用throw)，抛出给了catch中的参数, 
           则在try中代码就不会再继续执行下去，直接跳转到catch中去执行， catch中执行完成，
           再继续向下执行

	注意：在catch中提示发生了什么异常，这不是主要我们要做事，需要在catch中解决这个异常， 如果解决不了，
           则输出给用户
 
 	二、自己定义一个异常类
 
 		作用：就是写一个或多个方法解决当发生这个异常时的处理方式
 
 		1. 自己定义异常类，必须是Exception(内置类)的子类,
 		2. Exception类中的只有构造方法和toString()可以重写， 其它都final

 	三、处理多个异常
 

    Exception异常父类只能在抛出异常提示用的作用(要解决抛出异常就得自己定义异常子类)

 

 Exception异常父类  提示消息  例子
 
           try{
               echo "1111111<br>";
                $file=@fopen("tmp.txt", "r");
                if(!$file){
                     throw new Exception("没有这个文件打开失败");
                }

               }catch(Exception $e){   $e =new Exception();
                    echo $e->getMessage()."<br/>";
                     echo "22222222<br>";
               }

               echo "33333333";
 


自己定义异常子类的例子
 
 
                class openFileExceotion extends Exception{
	
                    function open(){
                         //touch  创建文件
                         touch("tem.text");
                         //fopen打开文件
                         $file=fopen("tem.text","r");
                         return $file;
                    }
               }	

               class DomExceotion extends Exception{
                    function dom(){
                         echo "处理dom发生异常";
                    }
               }


               class myClass{
                    function open(){
                         $file=@fopen("tem.text","r");
                         if(!$file){
                              throw new openFileExceotion("打开文件发生异常");
                         }
                    }
                  function dom($nul=0){
                      if(!$nul=0){
                          throw new DomExceotion("dom发生异常");
                      }
                  } 
               }

                 try{
                    $my=new myClass();
                    $my->open();
                    $my->dom(2);

                   }catch(openFileExceotion $e){
                  //提示异常信息 	
                     echo $e->getMessage()."<br/>";
                     //如果没有这个文件抛出异常，就调用open()方法解决异常
                     $e->open();

                    }catch(DomExceotion $e){
                           //提示异常信息 	
                      echo $e->getMessage()."<br/>";
                        //解决异常
                      $e->dom();
                  }

                   echo "33333333";



























