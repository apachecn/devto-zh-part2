# 通过 Swagger 自动生成 OpenAPI 文档的 Express API

> 原文：<https://dev.to/acanimal/express-api-with-autogenerated-openapi-doc-through-swagger-7na>

> 这篇文章最初发表在 acuriousanimal.com 的博客上。

在过去的几年里，OpenAPI 已经成为记录 API 的首选方式。在这篇文章中，我们将看到用 NodeJS 创建 API 并通过 [Swagger](https://swagger.io/) 工具表达是多么容易。

如果你在一个 REST API 中工作，你可能更希望有一些 API 文档，在那里你的用户可以找到你的 API 的端点，他们做什么，他们接受哪些参数，他们生成哪些输出。

> 观看加速视频:[https://www.youtube.com/watch?v=CE01dwNEkEU](https://www.youtube.com/watch?v=CE01dwNEkEU)

## 昂首阔步

[不要混淆 OpenAPI 和 Swagger](https://swagger.io/blog/api-strategy/difference-between-swagger-and-openapi/) 。OpenAPI 是一个说明 API 如何被文档化的规范。Swagger 是实现该规范的工具集合。

感谢 Swagger，见[编辑器示例](https://editor.swagger.io/)，写 API 文档并不难，你只需要写一堆 YAML 行就可以了。

在其他工具中，swagger 提供了 [swagger-ui](https://github.com/swagger-api/swagger-ui) ，它只不过是*一个 HTML、Javascript 和 CSS 资产的集合，可以从一个符合 swagger 的 API* 中动态生成漂亮的文档，或者换句话说，`swagger-ui`就是您在前面的 Swagger 编辑器链接中看到的漂亮的网页。

要提供`swagger-ui`内容，你只需要一个 web 服务器和捆绑在 JSON 或 YAML 文件中的 API 文档。

## ExpressJS 和 API 文档

当使用 ExpressJS 开发 API 时，我倾向于将我的 API 端点写在 *route* 文件中(通常也存储在`routes`文件夹下),该文件包含处理请求的规则，因此，它是记录我的 API 端点的最佳位置，例如:

```
/**
 * @swagger
 * /users:
 *    get:
 *      description: This should return all users
 */
app.get('/users', (req, res) => res.end('This sould return all users')); 
```

Enter fullscreen mode Exit fullscreen mode

问题是`swagger-ui`要求我所有的 API 文档驻留在一个文件中，即`swagger.json`，要美化成一个网页。

## 如何自动生成招摇单？

所有的魔力都存在于下一个包中:

*   [swagger-ui-express](https://github.com/scottie1984/swagger-ui-express) :向您的 express 应用程序添加中间件，以服务绑定到您的 swagger 文档的 Swagger UI。这相当于在应用程序中托管的 API 的动态文档。
*   [swagger-jsdoc](https://github.com/Surnet/swagger-jsdoc) :基于代码中的 jsdoc 注释生成 swagger doc，以保持一个活的、可重用的 OpenAPI (Swagger)规范。

所以这个想法是:

*   用 jsdoc 用斯瓦格·YAML 符号记录您的路线(正如您在前面的路线中看到的)。

*   让`swagger-jsdoc`自动生成一个`swagger.json`文件，其中包含您在文件中设置的所有文档。

```
const swaggerJsdoc = require('swagger-jsdoc');

const options = {
  swaggerDefinition: {
    // Like the one described here: https://swagger.io/specification/#infoObject
    info: {
      title: 'Test API',
      version: '1.0.0',
      description: 'Test Express API with autogenerated swagger doc',
    },
  },
  // List of files to be processes. You can also set globs './routes/*.js'
  apis: ['endpoints.js'],
};

const specs = swaggerJsdoc(options); 
```

Enter fullscreen mode Exit fullscreen mode

*   使用`swagger-ui-express`添加一个新的端点，用户可以在这里看到文档。

```
const swaggerUi = require('swagger-ui-express');

app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(specs)); 
```

Enter fullscreen mode Exit fullscreen mode

这就是神奇之处。此时，如果您在`http://localhost:3000/api-docs`启动并打开浏览器，您将看到 Swagger UI 网页，其中包含您的端点的文档。

当然，你可以创建更复杂的文档。您可以包含仅定义包含类型定义(即关于输入/输出数据)的文件，按标签对端点进行分组等。

重要的是`swagger-ui-express`和`swagger-jsdoc`的说服力如何能够极大地帮助和简化 API 文档的更新。