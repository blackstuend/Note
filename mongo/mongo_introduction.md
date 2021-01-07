# Mongo 

## Introduction
* Mongo 是一個由C++編譯而成的開源資料庫系統
* 使用類似JSON的結構組成
* 相比SQL，操作相對簡單，都是像使用function一樣的操作，好上手很多
* 有許多function都是使用Javascript寫成的如map,reduce
* 安裝簡單

## Install

* Windows

    * 前往[官網網站](https://www.mongodb.com/try/download/community)安裝
    * 切記 MongoDB Compass不要安裝,否則會延伸一些問題
    ![MongoDB Compass](./2020-12-24-154929.jpg)
    * 更改Database && log 位置
        * 創建在C:\data
        ```
        $ mkdir C:\data
        $ mkdir C:\data\db
        $ mkdir C:\data\log
        ```
        * 新增 mongod.log檔案進 C:\data\log
    * 接著去剛剛安裝db的位置新增配置檔案
    ![Db位置](https://github.com/blackstuend/Note/blob/master/mongo/2020-12-24-160129.jpg?raw=true)
    * 建立檔名:mongod.cfg
        * 如果沒有權限 建議先在桌面新增完在拉進去
        * systemLog：path 為前步驟 log 資料夾位置
        * storage：dbPath 為前步驟 db 資料夾位置
    ```
    systemLog:
        destination: file
        path: c:\data\log\mongod.log
    storage:
        dbPath: c:\data\db
    ```
    * 讓mongo 能夠吃到剛剛建立的cfg否則他還是會用預設
        * 預設db會在  C:\Program Files\MongoDB\Server\4.0\data
        * 預設log會在 C:\Program Files\MongoDB\Server\4.0\log


    * 啟動mongod Service
    ```
    $ "C:\Program Files\MongoDB\Server\4.0\bin\mongod.exe" --config "C:\Program Files\MongoDB\Server\4.0\mongod.cfg" --install
    ```
    * 如果有把mongod加入環境變數則直接打
    ```
    $ mongod --config "C:\Program Files\MongoDB\Server\4.0\mongod.cfg" --install
    ```
    
    * 加入install 日後使用與開啟就可以使用
        * 需使用administrator
    ```
    $ net start MongoDB
    $ net stop MongoDB
    ```

    * 進入mongodb操作

    ```shell
    $ "C:\Program Files\MongoDB\Server\4.0\bin\mongo.exe"
    ```

    * 加入環境變數


    ```
    $ mongo
    ```