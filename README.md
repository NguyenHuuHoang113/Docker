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

 **A container** :  một đối tượng thực thi của một image Docker.
 **Image** :  là một mẫu để tạo ra các container


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
Cách dung  : 
    <code>

        docker build [OPTIONS] PATH | URL | -

</code>

Ví du


Với **COMMAND** :
<br> - Để tạo một checkpoint từ container đang chạy :

    docker checkpoint create 

<br> - Để check danh sách checkpoints của container : 

    docker checkpoint ls

   và bên cạnh đó để check tất cả checkpoint đang up và exit :

    docker checkpoint ls -a 

<br> - Để xóa checkpoint :

    docker checkpoint rm

#### Docker images : dùng để kiểm tra list repo

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


#### Docker stop : dừng hoặc ngừng tất cả repo đang chạy 

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

#### Docker start : dùng để bắt đầu chạy CONTAINER

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
    
#### Docker build : 
Cách dùng : 

<code>

    docker build [OPTIONS] PATH | URL | -

</code>

#### Docker history : show lịch sử của một image
Cách dùng : 
<code>

    docker history <IMAGE>

 </code>
 Tương tự như sau : 
<code>

    C:\Users\Hoang\myapp\myapp>docker images
    REPOSITORY                        TAG                                        IMAGE ID       CREATED         SIZE
    my-repo/my-image                  lates                                      6ef8db98f260   45 hours ago    145MB
    hoangnh92/getting-started         latest                                     731e4e9fd554   2 days ago      318MB
    getting-started                   latest                                     731e4e9fd554   2 days ago      318MB
    <none>                            <none>                                     43b551fa5dd1   2 days ago      318MB
    httpd                             latest                                     daab1fa13f86   5 days ago      145MB
    docker                            latest                                     c365741dcfc2   5 days ago      311MB
    C:\Users\Hoang\myapp\myapp>docker history docker
    IMAGE          CREATED       CREATED BY                                      SIZE      COMMENT
    c365741dcfc2   5 days ago    /bin/sh -c #(nop)  CMD []                       0B
    <missing>      5 days ago    /bin/sh -c #(nop)  ENTRYPOINT ["dockerd-entr…   0B
    <missing>      5 days ago    /bin/sh -c #(nop)  EXPOSE 2375 2376             0B
    <missing>      5 days ago    /bin/sh -c #(nop)  VOLUME [/var/lib/docker]     0B
    <missing>      5 days ago    /bin/sh -c #(nop) COPY file:43a39857f9d05e4d…   7.65kB
    <missing>      5 days ago    /bin/sh -c set -eux;  wget -O /usr/local/bin…   1.68kB
    <missing>      5 days ago    /bin/sh -c #(nop)  ENV DIND_COMMIT=1f32e3c95…   0B
    <missing>      5 days ago    /bin/sh -c set -eux;   apkArch="$(apk --prin…   149MB
    <missing>      5 days ago    /bin/sh -c set -eux;  addgroup -S dockremap;…   4.77kB
</code>

#### Docker rename : đổi tên CONTAINER
Cách dùng : 
<code>

    docker rename [CONTAINER] <new.name>
</code>

Tương tự như sau : 
<code>

    C:\Users\Hoang\myapp\myapp>docker ps
    CONTAINER ID   IMAGE          COMMAND              CREATED        STATUS          PORTS                  NAMES
    51303185adb8   httpd:latest   "httpd-foreground"   46 hours ago   Up 49 minutes   0.0.0.0:8080->80/tcp   my-apache-container
    C:\Users\Hoang\myapp\myapp>docker rename 51303185adb8 NEW_NAME
    C:\Users\Hoang\myapp\myapp>docker ps
    CONTAINER ID   IMAGE          COMMAND              CREATED        STATUS          PORTS                  NAMES
    51303185adb8   httpd:latest   "httpd-foreground"   46 hours ago   Up 50 minutes   0.0.0.0:8080->80/tcp   NEW_NAME

</code>

#### Dockerr restart : khởi động lại CONTAINER
Cách dùng : 
<code>
    
    docker restart [OPTIONS] CONTAINER [CONTAINER...]
</code>
Tương tự như sau : 
    <code>

    C:\Users\Hoang\myapp\myapp>docker ps
    CONTAINER ID   IMAGE          COMMAND              CREATED        STATUS         PORTS                  NAMES
    51303185adb8   httpd:latest   "httpd-foreground"   46 hours ago   Up 9 seconds   0.0.0.0:8080->80/tcp   NEW_NAME

    C:\Users\Hoang\myapp\myapp>docker ps -a
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS                           PORTS                    NAMES
    51303185adb8   httpd:latest      "httpd-foreground"       46 hours ago   Up About a minute                0.0.0.0:8080->80/tcp     NEW_NAME
    bedbb327781b   nginx             "/docker-entrypoint.…"   47 hours ago   Exited (0) 9 hours ago                                    vigilant_herschel
    6d17809620ad   getting-started   "docker-entrypoint.s…"   2 days ago     Exited (255) About an hour ago   0.0.0.0:3000->3000/tcp   serene_bohr
    0b1bd5a7e442   ubuntu            "ls /"                   2 days ago     Exited (0) 9 hours ago                                    intelligent_zhukovsky
    1428058eb3e3   ubuntu            "bash -c 'shuf -i 1-…"   2 days ago     Exited (137) 9 hours ago                                  nostalgic_keller
    e123122caa9d   getting-started   "docker-entrypoint.s…"   2 days ago     Exited (0) 9 hours ago                                    charming_swirles

    C:\Users\Hoang\myapp\myapp>docker restart bedbb327781b
    bedbb327781b

    C:\Users\Hoang\myapp\myapp>docker ps
    CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS         PORTS                  NAMES
    51303185adb8   httpd:latest   "httpd-foreground"       46 hours ago   Up 2 minutes   0.0.0.0:8080->80/tcp   NEW_NAME
    bedbb327781b   nginx          "/docker-entrypoint.…"   47 hours ago   Up 6 seconds   0.0.0.0:80->80/tcp     vigilant_herschel
    </code>
#### Docker pause : tạm dừng CONTAINER đang chạy
Cách dùng :
<code>

     Docker pause [CONTAINER]
</code>
Tương tự như sau : 
<code>

    C:\Users\Hoang\myapp\myapp>docker ps
    CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS         PORTS                  NAMES
    51303185adb8   httpd:latest   "httpd-foreground"       46 hours ago   Up 2 minutes   0.0.0.0:8080->80/tcp   NEW_NAME
    bedbb327781b   nginx          "/docker-entrypoint.…"   47 hours ago   Up 6 seconds   0.0.0.0:80->80/tcp     vigilant_herschel
    C:\Users\Hoang\myapp\myapp>docker pause bedbb327781b
    bedbb327781b
</code>

![docker pause](/image.png)