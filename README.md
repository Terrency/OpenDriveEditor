# OpenDriveEditor
An OpenDrive Map Editor


#### Docker 启动编辑器指令
```bash
docker run --name mapdesigner -v /C/[Path_to_Project_Root]/OpenDriverEditor/distL
:/usr/share/nginx/html -p 80:80 nginx
```

#### 安装
```bash
#安装依赖
npm i
```

#### 打包
```bash
#打服务器包
npm run build
 
#打服务器包，不打static静态资源
npm run buildSimple

#打本地包，资源路径为/
npm run buildLocal
```
