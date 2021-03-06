###  Docker-compose  Nginx + Golang + Mysql + Redis + Composer

1. Install Dcoker
    - Docker
        - centos
            ```bash
            $ sudo yum install -y yum-utils
            $ sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
            $ sudo yum install docker-ce docker-ce-cli containerd.io
            ```
        - [Other systems](https://docs.docker.com/engine/install/)
    - Docker-compose
        - centos
            ```
            $ curl -L https://get.daocloud.io/docker/compose/releases/download/1.26.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
            $ sudo chmod +x /usr/local/bin/docker-compose
            # append to ~/.bashrc
            alias docker-compose="/usr/local/bin/docker-compose"
            
            $ source ~/.bashrc
            ```
        - [Other systems](https://docs.docker.com/compose/install/)

2. Start Docker Service (centos)
    ```
   $ sudo systemctl start docker
   $ sudo systemctl enable docker
   ```
3. Clone project
    - Git  `git clone https://github.com/KilluaChen/docker-golangl.git`
    - [Download](https://github.com/KilluaChen/docker-golang/archive/master.zip)
1. Create log dir
    ```
    $ cd docker-golang
    $ mkdir -p logs/error & mkdir -p logs/access
    ```
4. Append to `/etc/hosts` file (Optional)
    ```bash
     # Docker
     127.0.0.1       localhost
     127.0.0.1       test.pma.com
     ```
5. Command
    ```bash
   # Run
   $ docker-compose up

   # Start single service
   $ docker-compose up mysql
   
   # Run Daemon
   $ docker-compose up -d
   
   # Stop
   $ docker-compose stop
   
   # Delete
   $ docker-compose down
   ```
1. 阿里云加速
    ```bash
    sudo mkdir -p /etc/docker
    sudo tee /etc/docker/daemon.json <<-'EOF'
    {
      "registry-mirrors": ["https://c9uxfqpy.mirror.aliyuncs.com"]
    }
    EOF
    sudo systemctl daemon-reload
    sudo systemctl restart docker
    ```
6. Visit
    - Localhost [http://localhost](http://localhost/index.html)
    - PhpMyAdmin [http://test.pma.com](http://test.pma.com)
1. zsh alias
    ```bash
    #Git
    alias gaa="git add ."
    alias gc="git commit -m"
    alias gp="git push"
    alias gd="git diff"
    alias gs="git status"
    alias gcm="git checkout master"
    alias gcd="git checkout dev"
    alias gb="git branch"

    #Docker
    alias dc="docker-compose"
    alias dis="docker images"
    alias dps="docker ps"
    ```
7. PS
    - 确保`80`,`3306`,`6479`端口没有被占用
    - 下载`Docker 镜像`过慢可以使用阿里的[容器镜像服务](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors) 
    - 如果挂载的目录没有权限,需要添加file sharing 
        > You can configure shared paths from Docker -> Preferences... -> File Sharing.
    - 更多设置参考 [https://github.com/nanoninja/docker-nginx-php-mysql](https://github.com/nanoninja/docker-nginx-php-mysql)
    
     
    
