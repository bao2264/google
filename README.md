### React SSR 

- 客户端渲染存在的问题
  - 首屏等待时间长，用户体验差
  - 页面结构为空，不利于SEO
- 同构
  - 指代码复用，即实现客户端和服务端代码最大限度的重用
- 实现简单的react ssr
  - 引入要渲染的react的组件
  - 通过renderToString（导出自react-dom/server）方法将react组件转换为html字符串
  - 将转换后的字符串返回给客户端
- 客户端react添加事件
  - 使用hydrate方法对组件进行渲染，为组件添加事件
  - hydrate方法在实现渲染的时候，会复用原本已经存在的DOM节点，减少重新生成节点以及删除原本DOM节点的开销。
  - 将打包好的客户端js文件，附加到返回给请求的html文件中
- 优化
  - 可以使用webpack-merge工具对相同的配置进行优化
  - 使用npm-run-all工具对启动命令进行优化
  - 使用webpack-node-external工具对服务端代码进行打包体积优化
- 添加路由
  - 分别实现客户端、服务端路由，客户端用于支持用户点击跳转，服务端用于直接输入页面地址
  - 使用数组形式的配置路由
- redux
  - 客户端使用正常的redux工作流
  - 服务端在接收到请求的时候创建store,并在渲染组件之前获取组件所需要的数据
    - 组件中添加获取数据的方法，供服务端调用
    - 将方法保存在路由配置信息中
    - 服务端接收到请求后，根据请求地址匹配路由信息
    - 从路由信息中拿到获取数据的方法
    - 调用方法获取数据，渲染组件并返回结果给客户端
  - 
- 

