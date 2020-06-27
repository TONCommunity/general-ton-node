
## ton测试链搭建流程

### 编译docker

    git clone https://github.com/debuggor/general-ton-node.git
    cd general-ton-node
    git checkout debuggor
    docker build -t ton-private-network .

### 运行

    安装 docker-compose
    运行：docker-compose up -d
    查看日志：docker logs genesis -f
            docker logs node_2 -f
    终止： docker-compose down
    
## 操作
    
    进入： docker exec -it genesis bash
    导出json： cat my-ton-global.config.json
    退出： exit
    交互:
        validator-engine-console -k client -p server.pub -a 127.0.0.1:8827
        lite-client -a 127.0.0.1:8828 -p liteserver.pub
  
### 问题

    1、合约里初始化地址 Pu开头的地址如何生成？能生成Pu开头地址，但Pu转换回的正常地址没在掌控中；应该是生成PU地址的方式不对；
    PU前缀：0x3ee6 
   
    2、docker-compose.yml 改genesis的ip地址后，其他两个节点无法同步；不做改动，能正常同步；

### todo

    1、搞清楚Pu地址的生成方式，初始区块时让地址有币，做转账测试；
    2、搭建其他验证节点，并能正常同步
    
### 其他

    修改gen-zerostate.fif文件，测试初始化
    cd /var/ton-work/contracts
    ./create-state gen-zerostate.fif  
    
