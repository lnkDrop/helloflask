# 《Flask web 开发实战》学习笔记
## 此书github地址:[《Flask Web 开发实战》](https://github.com/greyli/helloflask)

## 发现
* 处理异常插件：SENTRY(哨兵)  [教程](https://segmentfault.com/a/1190000014847638)
* Google的一款绘制流程图插件:Gliffy Diagrams ；在Chrome商店里下载使用
***
## 笔记
##### 注：2020年不再维护python2版本，故使用python3.3以上
##### 需要安装包：
1. Flask
2. pip
3. Pipenv
4. Virtualenv
5. Pipfile
6. python-dotenv
7. Watchdog 
### 一、Web前端结构

1. **HTML** --------结构层
2. **CSS** (简化编写样式的操作)---------表现层(使用框架:[Bootstrap](https://getbootstrap.com))
3. **JavaScript**(触发器，动画效果) -------行为层(使用库:[jQuery](https://jquery.com/))

### 二、hello flask
* 项目目录中创建并运行虚拟环境
  ``` 
  pipenv install 
  pipenv shell
   ```
* 虚拟环境中安装Flask
  ```
  pipenv install flask
  ```
* 实例app
  ```
  app=Flask(__name__)
  ```
    ### 注册路由,/根目录，url规则(指向某个资源的地址)
  ```
  www./(根)/x(绝对地址)
  ```
  ```
  @实例.route('/')
  ```
  ### 绑定多个URL(访问hi和hello这两个url，返回同一视图)
  ```
  @app.route('/hi')
  ```
  ```
  @app.route('/hello')
  ```
  ### 动态URL(hi/(name)),name可以是变量，可以进行动态访问,访问的视图随着name的变化而变化
  ```
  @app.route('/hi/<name>')
  ```
  ### 为防止404错误，在route(hi/name)里设置变量默认值
  ```
  @app.route('/hi', defaults={'name': 'Programmer'})
  @app.route('/hi/<name>')
  def hi(name):
    return '<h1>Hello, %s!</h1>' % name
  ```
    ### 此时会返回Hello,Programmer

### 三、启动开发服务器
