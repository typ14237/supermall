# supermall

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
### 目录的解析
  src
    /assets--放置静态资源文件(图片以及css)
    /common--放置公共的js文件(公共变量等)
    /components--组件
      /common--放可以重复利用的组件(通用组件)
      /content--只能在该项目中使用的组件(业务组件)
    /network--网络设置
    /router--路由设置
    /store--Vuex设置
    /view--界面设置