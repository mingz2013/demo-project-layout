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



### 一个模板参考



https://github.com/golang-standards/project-layout