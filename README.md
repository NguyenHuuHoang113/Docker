## **Introduction Docker**
***
### **Table of content**
***
####
* Link bài viết : 
* Link nguồn tham khảo : 
* 
### **Introduction** : 
 **Docker** : một  open platform của developing, shipping, and running applications ,  a technology cho phép  us to wrap ứng dụng  ___one package___, which are ___portable___ (run anywhere) and ___executable___ (run anytime).

 **A container** : là quá trình chạy trên máy chủ


### **Docker run reference** 
#### Docker run :  là một lệnh trong Docker CLI (Command Line Interface) được sử dụng để chạy một container từ một image
<br> Cách dùng :
 <code>

     docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
</code>

Trong do : 
    * **OPTIONS** : Các tùy chọn để định cấu hình container, ví dụ như cổng kết nối, biến môi trường, quyền truy cập vào volume, và nhiều hơn nữa.
    * **IMAGE**: Docker image mà bạn muốn chạy container từ.
    * **COMMAND**: Lệnh mà bạn muốn chạy trong container.
    * **ARG**: Các đối số cho lệnh được chỉ định trong **COMMAND**

Vi du : ta se chay một container Nginx và liên kết cổng của container với cổng của máy host.
<br>
    Đầu tiên, bạn cần phải tải image của Nginx bằng lệnh:
<code>

    docker pull nginx
</code> 
Ket qua : 

<code>

    C:\Users\Hoang>docker pull nginx
    Using default tag: latest
    latest: Pulling from library/nginx
    3f9582a2cbe7: Pull complete
    9a8c6f286718: Pull complete
    e81b85700bc2: Pull complete
    73ae4d451120: Pull complete
    6058e3569a68: Pull complete
    3a1b8f201356: Pull complete
    Digest: sha256:aa0afebbb3cfa473099a62c4b32e9b3fb73ed23f2a75a65ce1d4b4f55a5c2ef2
    Status: Downloaded newer image for nginx:latest
    docker.io/library/nginx:latest

</code>

<br> Sau khi tải xong image, bạn có thể sử dụng lệnh " ***docker run*** " để chạy container từ image đã tải về:
<code>


        docker run -d -p 80:80 nginx

</code>

Ket qua : se duoc in ra mot [container ID]
<code>

    C:\Users\Hoang>docker run -d -p 80:80 nginx
    bedbb327781b17e03fe484e0d5c49df9aa3388f838daf3ba018c0c6a4fd039ae
</code>
<br> Trong đó:

     -d: Chạy container ở chế độ detach (ngầm), tức là chạy container trong nền và hiển thị ID của container.
     -p 80:80 : Liên kết cổng 80 của container với cổng 80 của máy host.
     nginx: Tên image được sử dụng để khởi tạo container.


> NOTE : chung ta co the kiem tra thong tin  ***CONTAINER*** bang cach : *docker ps* 

![docker ps ](/docker%20ps.png)


#### Use the Docker command line docker

### **Docker** 
***
#### Docker attach : được sử dụng để gắn kết một tiến trình đang chạy trong một container Docker và kết nối input/output của terminal hiện tại với tiến trình đó. 

<br> Cach dung : 

   <code>
    
        docker attach [OPTIONS] <container>

   </code>

Vi du

#### Docker build : được sử dụng để tạo một Docker image mới từ một Dockerfile . 
Cách dung : 
    
        docker build [OPTIONS] PATH | URL | -


Với **COMMAND** :
<br> - Để tạo một checkpoint từ container đang chạy :

    docker checkpoint create 

<br> - Để check danh sách checkpoints của container : 

    docker checkpoint ls

   và bên cạnh đó để check tất cả checkpoint đang up và exit :

    docker checkpoint ls -a 

<br> - Để xóa checkpoint :

    docker checkpoint rm

Docker images : dùng để kiểm tra list repo

Cách dùng : 

<code>

    docker images [OPTIONS] [REPOSITORY[:TAG ]]
</code>

Ví dụ bạn muốn kiểm tra danh sách repo mà mình đang có bạn sẽ làm như sau : 
 
<code>

        C:\Users\Hoang>docker image ls
        REPOSITORY                        TAG                 IMAGE ID       CREATED         SIZE
        my-repo/my-image                  lates              6ef8db98f260   35 hours ago    145MB
        hoangnh92/getting-started         latest             731e4e9fd554   46 hours ago    318MB
        getting-started                   latest             731e4e9fd554   46 hours ago    318MB
</code>


Docker stop : dừng hoặc ngừng tất cả repo đang chạy 

Cách dùng : 
<code>

    docker stop [OPTIONS] CONTAINER [CONTAINER...]

</code>

ví dụ bạn muốn tạm dừng 1 CONTAINER đang chạy : 
<code>
        C:\Users\Hoang>docker ps
        CONTAINER ID   IMAGE          COMMAND              CREATED        STATUS       PORTS                  NAMES
        51303185adb8   httpd:latest   "httpd-foreground"   37 hours ago   Up 2 hours   0.0.0.0:8080->80/tcp   my-apache-container

        C:\Users\Hoang>docker stop 51303185adb8
        51303185adb8

    </code>

    Docker start : dùng để bắt đầu chạy CONTAINER

    Cách dùng : 
    <code>

    docker start [OPTIONS] CONTAINER [CONTAINER...]
    </code>

    Ví dụ :bạn muốn khởi chạy một container
    <code>
    C:\Users\Hoang>docker ps
    CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

    C:\Users\Hoang>docker ps -a
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS                            PORTS     NAMES
    51303185adb8   httpd:latest      "httpd-foreground"       37 hours ago   Exited (0) About a minute ago               my-apache-container
    bedbb327781b   nginx             "/docker-entrypoint.…"   38 hours ago   Exited (0) About a minute ago               vigilant_herschel

    C:\Users\Hoang>docker start 6d17809620ad
    6d17809620ad

    C:\Users\Hoang>docker ps
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS         PORTS                    NAMES
    6d17809620ad   getting-started   "docker-entrypoint.s…"   39 hours ago   Up 5 seconds   0.0.0.0:3000->3000/tcp   serene_bohr
    </code>
    
    