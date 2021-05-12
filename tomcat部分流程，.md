通过复制粘贴原文件进行更名，

![image-20210428154345491](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210428154345491.png)



该文件由于是文件夹，复制指令

cp -r 文件夹名 目标路径

复制一个以后，使用剪切进行重命名。

![image-20210428161505715](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210428161505715.png)

重命名后，需要通i过文档进行修改端口，避免冲突，具体文档路径为：

![image-20210428161809481](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210428161809481.png)

![image-20210428161834789](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210428161834789.png)

vi/vim 进入该文档，进行端口修改，下图为关闭端口

![image-20210428161929276](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210428161929276.png)

下图为开启端口。

![image-20210428162147108](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210428162147108.png)

注：端口不可冲突。

修改好以后，为了区分3个文档，需要进行自定义标题修改，每一个都要修改

vim tomcat/webapps/ROOT/index.jsp

![image-20210428162839191](C:\Users\Administrator\Desktop\image-20210428162839191.png)

​	

全部修改完成后进行激活，将3个./tomcat8080/bin/startup.sh，分别激活。

激活，激活成功后通过ps -ef | grep java 

检查进程。

