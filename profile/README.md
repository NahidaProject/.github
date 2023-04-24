# Nahida Project

# 2023.04.24: 当前项目停止开发，请移步新项目[KeQing Anime](https://github.com/KeQingAnime)

## 来访者, 你好呀 😊

NahidaProject Anime 是动漫门户管理系统

## 通过 Docker 部署

### 1. 数据库配置

- 当前目录新建`mysql`文件夹

将数据库脚本`anime.sql`放入该文件夹

### 2. docker-compose 配置

- 当前目录新建`docker-compose.yml`

```yaml
version: "3.9"
services:
  anime_frontend:
    build: NahidaProject_Anime_Frontend
    ports:
      - "5173:5173"
  anime_backend:
    build: NahidaProject_Anime_Backend
    ports:
      - "1314:1314"
    volumes:
      - /d:/data
    environment:
      - SPRING_DATASOURCE_URL=jdbc:mysql://db/anime?serverTimezone=UTC
      - SPRING_DATASOURCE_USERNAME=root
      - SPRING_DATASOURCE_PASSWORD=123456
  db:
    image: mysql:latest
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=123456
      - MYSQL_DATABASE=anime
    volumes:
      - ./mysql:/docker-entrypoint-initdb.d
```

### 3. 目录结构

```
> mysql
    > anime.sql
> NahidaProject_Anime_Backend
    > ...
> NahidaProject_Anime_Frontend
    > ...
> docker-compose.yml
```

### 4. 部署项目

当前路径下执行`docker-compose up --build`

## 管理平台:

![management](https://raw.githubusercontent.com/NahidaProject/NahidaProject_Anime_Management/1.1/index.png)  
![managementmain](https://raw.githubusercontent.com/NahidaProject/NahidaProject_Anime_Management/1.1/main.png)

## 前端:

Bootstrap:
![Bootstrap](https://raw.githubusercontent.com/NahidaProject/NahidaProject_Anime_Frontend/bootstrap/index.png "index.png")
Vanilla:
![frontend](https://raw.githubusercontent.com/NahidaProject/NahidaProject_Anime_Frontend/main/index.png)
