## **Introduction Docker**
***
### **Table of content**
***
####
- [**Introduction Docker**](#introduction-docker)
  - [**Table of content**](#table-of-content)
    - [](#)
  - [**Introduction** :](#introduction-)
  - [**Docker run reference**](#docker-run-reference)
    - [Docker run : được sử dụng để chạy một container từ một image](#docker-run--được-sử-dụng-để-chạy-một-container-từ-một-image)
  - [**Docker**](#docker)
    - [Docker attach : được sử dụng để gắn kết một tiến trình đang chạy trong một container Docker và kết nối input/output của terminal hiện tại với tiến trình đó.](#docker-attach--được-sử-dụng-để-gắn-kết-một-tiến-trình-đang-chạy-trong-một-container-docker-và-kết-nối-inputoutput-của-terminal-hiện-tại-với-tiến-trình-đó)
    - [Docker images : dùng để kiểm tra list repo](#docker-images--dùng-để-kiểm-tra-list-repo)
    - [Docker start : dùng để bắt đầu chạy CONTAINER](#docker-start--dùng-để-bắt-đầu-chạy-container)
    - [Docker build :](#docker-build-)
    - [Docker history : show lịch sử của một image](#docker-history--show-lịch-sử-của-một-image)
    - [Docker rename : đổi tên CONTAINER](#docker-rename--đổi-tên-container)
    - [Dockerr restart : khởi động lại CONTAINER](#dockerr-restart--khởi-động-lại-container)
    - [Docker stop  : tạm dừng CONTAINER đang chạy](#docker-stop---tạm-dừng-container-đang-chạy)
    - [Docker rm: dùng để xóa ***CONTAINER***](#docker-rm-dùng-để-xóa-container)
    - [Docker logs :](#docker-logs-)
    - [Docker login : đăng nhập vào CONTAINER](#docker-login--đăng-nhập-vào-container)
    - [Docker pull :](#docker-pull-)
    - [Docker push : dùng để update image đến a registry](#docker-push--dùng-để-update-image-đến-a-registry)
### **Introduction** : 
 **Docker** : một  open platform của developing, shipping, and running applications ,  a technology cho phép  us to wrap ứng dụng  ___one package___, which are ___portable___ (run anywhere) and ___executable___ (run anytime).

 **A container** :  một đối tượng thực thi của một image Docker.
 **Image** :  là một mẫu để tạo ra các container


### **Docker run reference** 
#### Docker run : được sử dụng để chạy một container từ một image
<br> Cách dùng :
 <code>

     docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
</code>

Trong do : 
    * **OPTIONS** : Các tùy chọn để định cấu hình container, ví dụ như cổng kết nối, biến môi trường, quyền truy cập vào volume, và nhiều hơn nữa.
    * **IMAGE**: Docker image mà bạn muốn chạy container từ.
    * **COMMAND**: Lệnh mà bạn muốn chạy trong container.
    * **ARG**: Các đối số cho lệnh được chỉ định trong **COMMAND**

Vi du : Để  một container Nginx và liên kết cổng của container với cổng của máy host.
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

### **Docker** 
***
#### Docker attach : được sử dụng để gắn kết một tiến trình đang chạy trong một container Docker và kết nối input/output của terminal hiện tại với tiến trình đó. 

<br> Cach dung : 

   <code>
    
        docker attach [OPTIONS] <CONTAINER>

   </code>

Tương tự như sau : 
<code>

    C:\Users\Hoang>docker attach test
    / # ls
    bin    dev    etc    home   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    tmp    usr    var
</code>

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
    <missing>      5 days ago    /bin/sh -c set -eux;   apkArch="$(apk --prin…  ) 149MB
    <missing>      5 days ago    /bin/sh -c set -eux;  addgroup -S dockremap;…   4.77kB ]
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
    
    docker restart <CONTAINER>
</code>
Tương tự như sau : 
<code>

    C:\Users\Hoang\myapp\myapp>docker ps -a
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS                           PORTS                    NAMES
    51303185adb8   httpd:latest      "httpd-foreground"       46 hours ago   Up About a minute                0.0.0.0:8080->80/tcp     NEW_NAME
    bedbb327781b   nginx             "/docker-entrypoint.…"   47 hours ago   Exited (0) 9 hours ago                                    vigilant_herschel
    C:\Users\Hoang\myapp\myapp>docker restart bedbb327781b
    bedbb327781b
    C:\Users\Hoang\myapp\myapp>docker ps
    CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS         PORTS                  NAMES
    51303185adb8   httpd:latest   "httpd-foreground"       46 hours ago   Up 2 minutes   0.0.0.0:8080->80/tcp   NEW_NAME
    bedbb327781b   nginx          "/docker-entrypoint.…"   47 hours ago   Up 6 seconds   0.0.0.0:80->80/tcp     vigilant_herschel
 </code>
#### Docker stop  : tạm dừng CONTAINER đang chạy
Cách dùng :
<code>

     Docker stop <CONTAINER>
</code>
Tương tự như sau : 
<code>

    C:\Users\Hoang>docker ps -a
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS                      PORTS                    NAMES
    51303185adb8   httpd:latest      "httpd-foreground"       4 days ago     Up 12 hours                 0.0.0.0:8080->80/tcp     NEW_NAME
    bedbb327781b   nginx             "/docker-entrypoint.…"   5 days ago     Exited (255) 12 hours ago   0.0.0.0:80->80/tcp       vigilant_herschel
	C:\Users\Hoang>docker stop 51303185adb8
	51303185adb8
	C:\Users\Hoang>docker ps -a
	CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS                      PORTS                    NAMES
	51303185adb8   httpd:latest      "httpd-foreground"       4 days ago     Exited (0) 11 seconds ago                            NEW_NAME
	bedbb327781b   nginx             "/docker-entrypoint.…"   5 days ago     Exited (255) 12 hours ago   0.0.0.0:80->80/tcp       vigilant_herschel
</code>

#### Docker rm: dùng để xóa ***CONTAINER***
<br> Cách dùng : 
<code>

    docker rm <Container>

</code>
Tương tự như sau : 

<code>

    C:\Users\Hoang>docker ps -a
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS                      PORTS                    NAMES
    51303185adb8   httpd:latest      "httpd-foreground"       4 days ago     Exited (0) 11 seconds ago                            NEW_NAME
    C:\Users\Hoang>docker rm 51303185adb8
    51303185adb8
    C:\Users\Hoang>docker ps -a
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS                      PORTS                    NAMES

</code>
<br>

> NOTE : CONTAINER bạn xóa phải ở trạng thái "STOP"  bạn có thể đọc cách stop [`docker stop`](#docker-stop--tạm-dừng-container-đang-chạy).
    Nếu CONTAINER đang ở chạy thái "UP" khi bạn xóa thì nó sẽ hiện ra như này :
    
    Error response from daemon: You cannot remove a running container e7bfa2daf3468b97e4eb11c225862af5a42e144dfe935826c8c3110d4be275c2. Stop the container before attempting removal or force remove

#### Docker logs : 
<br> Cách dùng : hiển thị log của một ***CONTAINER*** 
<code>

    docker logs <CONTAINER>
</code>

Tương tự như sau : 
<code>

    C:\Users\Hoang>docker ps
    CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS             PORTS                    NAMES
    e7bfa2daf346   httpd:latest      "httpd-foreground"       12 hours ago   Up 12 hours        80/tcp                   naughty_burnell
    e123122caa9d   getting-started   "docker-entrypoint.s…"   5 days ago     Up About an hour   0.0.0.0:3001->3000/tcp   charming_swirles
    C:\Users\Hoang>docker logs e123122caa9d
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
</code> 

#### Docker login : đăng nhập vào CONTAINER 
Cách dùng : 
<code> 
    
    docker login <CONTAINER>


#### Docker pull : 
Cách dùng : Để download một image từ a registry
<code>
    docker  pull <name image>
</code>
Tương tự như sau : 
        ví dụ tôi muốn download image của nginx : 
        
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


#### Docker push : dùng để update image đến a registry
Cách dùng : 
<code>

    C:\Users\Hoang>docker push nginx
    Using default tag: latest
    The push refers to repository [docker.io/library/nginx]
    101af4ba983b: Layer already exists
    d8466e142d87: Layer already exists
    83ba6d8ffb8c: Layer already exists
    e161c82b34d2: Layer already exists
    4dc5cd799a08: Layer already exists
    650abce4b096: Waiting
    denied: requested access to the resource is denied
    C:\Users\Hoang>docker tag nginx hoangnh92/huuhoang
    C:\Users\Hoang>docker push hoangnh92/huuhoang
    Using default tag: latest
    The push refers to repository [docker.io/hoangnh92/huuhoang]
    101af4ba983b: Mounted from library/nginx
    d8466e142d87: Mounted from library/nginx
    83ba6d8ffb8c: Mounted from library/nginx
    e161c82b34d2: Mounted from library/nginx
    4dc5cd799a08: Mounted from library/nginx
    650abce4b096: Pushed
    latest: digest: sha256:942ae2dfd73088b54d7151a3c3fd5af038a51c50029bfcfd21f1e650d9579967 size: 1570
</code>

Docker tag : 
Cách dùng : 
<code>

</code>

Tương tự như sau :

Docker volume : quản lý volumes
Cách dùng : 

<code>

    docker volume <COMMAND> 
</code>

Tương tự như sau : 

- Để tạo volume : 

<code>

    docker volume create <NAME_VOLUME>
</code>
     
     Ví dụ : tạo một volume tên là "Hello"

     <code> 

     C:\Users\Hoang>docker volume create hello
    hello
    </code>

- Để check list volumes : 

<code>

    C:\Users\Hoang>docker volume list
    DRIVER    VOLUME NAME
    local     556c7103312534d7ae171fe3d3550f0de8f0fefa12b3fe36e461f0e38dd7e062
    local     hello
    local     todo-db
    local     volume-github
</code>

- Để xóa volumes : 

Cách dùng : 

<code>

    docker volume rm <NAME_VOLUME>
</code>

Tương tự như sau : 

<code> 

    C:\Users\Hoang>docker volume list
    DRIVER    VOLUME NAME
    local     556c7103312534d7ae171fe3d3550f0de8f0fefa12b3fe36e461f0e38dd7e062
    local     hello
    local     todo-db
    local     volume-github
    C:\Users\Hoang>docker volume rm 556c7103312534d7ae171fe3d3550f0de8f0fefa12b3fe36e461f0e38dd7e062
    556c7103312534d7ae171fe3d3550f0de8f0fefa12b3fe36e461f0e38dd7e062
    C:\Users\Hoang>docker volume list
    DRIVER    VOLUME NAME
    local     hello
    local     todo-db
    local     volume-github
</code>
