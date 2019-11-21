# demo-project
demo-project




# 关于架构演进的探讨


## 架构的演进


### 单文件阶段
```tree
 demo-project (master) ✗ tree
.
├── README.md
└── app.py

0 directories, 2 files
 demo-project (master) ✗ 
```


只有一个模块，所有代码都写到一个模块里面


### 简单拆分

```tree
 demo-project (master) ✗ tree
.
├── README.md
├── app.py
├── conf.py
├── controller.py
├── dao.py
├── db.py
├── model.py
└── service.py

0 directories, 8 files
 demo-project (master) ✗ 
```

很多同学在这一步不知道如何拆分，或者拆分的不够彻底。

最糟糕的写法是一个函数里写完一切。

不知道如何拆分，导致函数太长。导致模块太长。


### 多接口

```tree
 demo-project (master) ✗ tree
.
├── README.md
├── app.py
├── conf.py
├── controller
│   ├── __init__.py
│   ├── controller.py
│   └── controller2.py
├── dao.py
├── db.py
├── model
│   ├── __init__.py
│   └── model.py
└── service
    ├── __init__.py
    ├── service.py
    └── service2.py

3 directories, 13 files
 demo-project (master) ✗ 
```

按照功能接口的类别，拆分成不同的模块。


### 抽离公共模块

```tree
 demo-project (master) ✗ tree
.
├── README.md
├── app.py
├── common
│   ├── __init__.py
│   └── db.py
├── conf.py
├── controller
│   ├── __init__.py
│   ├── controller.py
│   └── controller2.py
├── dao.py
├── model
│   ├── __init__.py
│   └── model.py
└── service
    ├── __init__.py
    ├── service.py
    └── service2.py

4 directories, 14 files
 demo-project (master) ✗ 
```

将公用的模块抽离。


### 多app阶段

```tree
 demo-project (master) ✗ tree
.
├── README.md
├── app
│   ├── __init__.py
│   ├── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
├── app.py
├── app2
│   ├── __init__.py
│   ├── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
└── common
    ├── __init__.py
    └── db.py

9 directories, 26 files
 demo-project (master) ✗ 
```

不同的大的系统，拆分不同的大的模块。


### 抽离公共模块

```tree
 demo-project (master) ✗ tree
.
├── README.md
├── app
│   ├── __init__.py
│   ├── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
├── app.py
├── app2
│   ├── __init__.py
│   ├── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
└── common
    ├── __init__.py
    ├── conf
    │   ├── __init__.py
    │   ├── conf.py
    │   └── conf2.py
    ├── dao
    │   ├── __init__.py
    │   ├── dao.py
    │   └── dao2.py
    ├── db.py
    ├── model
    │   ├── __init__.py
    │   ├── model.py
    │   └── model2.py
    └── service
        ├── __init__.py
        ├── service.py
        └── service2.py

13 directories, 38 files
 demo-project (master) ✗ 
```

大的系统模块要抽离公用代码。


### 改造微服务
```tree
 demo-project (master) ✗ tree
.
├── Makefile
├── README.md
├── app
│   ├── __init__.py
│   ├── app.py
│   ├── conf
│   │   ├── __init__.py
│   │   └── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao
│   │   ├── __init__.py
│   │   └── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
├── app2
│   ├── __init__.py
│   ├── app.py
│   ├── conf
│   │   ├── __init__.py
│   │   └── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao
│   │   ├── __init__.py
│   │   └── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
└── common
    ├── __init__.py
    ├── conf
    │   ├── __init__.py
    │   ├── conf.py
    │   └── conf2.py
    ├── dao
    │   ├── __init__.py
    │   ├── dao.py
    │   └── dao2.py
    ├── db.py
    ├── model
    │   ├── __init__.py
    │   ├── model.py
    │   └── model2.py
    └── service
        ├── __init__.py
        ├── service.py
        └── service2.py

17 directories, 44 files
 demo-project (master) ✗ 
```

改造微服务，只需要将每个app分配一个可执行文件就好了。

### 使用docker


```tree
 demo-project (master) ✗ tree
.
├── Makefile
├── README.md
├── app
│   ├── Dockerfile
│   ├── __init__.py
│   ├── app.py
│   ├── conf
│   │   ├── __init__.py
│   │   └── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao
│   │   ├── __init__.py
│   │   └── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
├── app2
│   ├── Dockerfile
│   ├── __init__.py
│   ├── app.py
│   ├── conf
│   │   ├── __init__.py
│   │   └── conf.py
│   ├── controller
│   │   ├── __init__.py
│   │   ├── controller.py
│   │   └── controller2.py
│   ├── dao
│   │   ├── __init__.py
│   │   └── dao.py
│   ├── model
│   │   ├── __init__.py
│   │   └── model.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
├── common
│   ├── __init__.py
│   ├── conf
│   │   ├── __init__.py
│   │   ├── conf.py
│   │   └── conf2.py
│   ├── dao
│   │   ├── __init__.py
│   │   ├── dao.py
│   │   └── dao2.py
│   ├── db.py
│   ├── model
│   │   ├── __init__.py
│   │   ├── model.py
│   │   └── model2.py
│   └── service
│       ├── __init__.py
│       ├── service.py
│       └── service2.py
└── docker-compose.yml

17 directories, 47 files
 demo-project (master) ✗ 
```

使用docker，只需要在每个app里面写个Dockerfile，最外层用docker-compose.yml控制。

一定要记得，有个Makefile，封装命令的调用。

### 使用k8s


```tree
 demo-project (master) ✗ tree
.
├── Makefile
├── README.md
├── development
│   ├── docker-compose.yml
│   └── k8s.yml
└── source
    ├── apps
    │   ├── __init__.py
    │   ├── app
    │   │   ├── Dockerfile
    │   │   ├── __init__.py
    │   │   ├── app.py
    │   │   ├── conf
    │   │   │   ├── __init__.py
    │   │   │   └── conf.py
    │   │   ├── controller
    │   │   │   ├── __init__.py
    │   │   │   ├── controller.py
    │   │   │   └── controller2.py
    │   │   ├── dao
    │   │   │   ├── __init__.py
    │   │   │   └── dao.py
    │   │   ├── model
    │   │   │   ├── __init__.py
    │   │   │   └── model.py
    │   │   └── service
    │   │       ├── __init__.py
    │   │       ├── service.py
    │   │       └── service2.py
    │   └── app2
    │       ├── Dockerfile
    │       ├── __init__.py
    │       ├── app.py
    │       ├── conf
    │       │   ├── __init__.py
    │       │   └── conf.py
    │       ├── controller
    │       │   ├── __init__.py
    │       │   ├── controller.py
    │       │   └── controller2.py
    │       ├── dao
    │       │   ├── __init__.py
    │       │   └── dao.py
    │       ├── model
    │       │   ├── __init__.py
    │       │   └── model.py
    │       └── service
    │           ├── __init__.py
    │           ├── service.py
    │           └── service2.py
    └── common
        ├── __init__.py
        ├── conf
        │   ├── __init__.py
        │   ├── conf.py
        │   └── conf2.py
        ├── dao
        │   ├── __init__.py
        │   ├── dao.py
        │   └── dao2.py
        ├── db.py
        ├── model
        │   ├── __init__.py
        │   ├── model.py
        │   └── model2.py
        └── service
            ├── __init__.py
            ├── service.py
            └── service2.py

20 directories, 49 files
 demo-project (master) ✗ 
```


进一步整理，将代码独立一个目录，部署文件单独一个目录。顺便集成k8s部署。


### 一个模板参考



https://github.com/golang-standards/project-layout