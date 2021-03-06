
# Mongoose

> mongoose是mongoDB的一个对象模型工具，是基于node-mongodb-native开发的mongoDB的nodejs驱动，可以在异步的环境下执行。同时它也是针对mongoDB操作的一个对象模型库，封装了mongoDB对文档的一些增删改查等常用方法，让nodejs操作mongoDB数据库变得更加容易。

### Mongoose()
构造函数 Mongoose

```javascript
var mongoose = require('mongoose');
```

mongoose 模块的 exports 对象是此类的一个实例。大多数应用只会使用这一个实例。

### Mongoose.prototype.Mongoose()
此方法可以创建另一个 Mongoose 实例。

Example:

```javascript
var mongoose = require('mongoose');
var anotherMongoose = new mongoose.Mongoose();
```

### Mongoose.prototype.Connection()
mongoose 连接，一个 Connection 相当于一个数据库。
### Mongoose.prototype.createConnection()
创建一个 Connection 实例。每个 connection 实例映射到一个数据库。在分割多个数据库连接时，此方法很有用。

Connection 是一个 thenable 对象，可以这样使用`await mongoose.createConnection()`
参数：（传递的选项优先于连接字符串中包含的选项。）
- uri: a mongodb:// URI
- options: 传递给MongoDB驱动程序的connect()函数，除了下面解释的4个mongoose特定选项。
  - options.user: 用于身份认证的用户名
  - options.pass: 用于身份认证的密码
  - options.autoIndex=true: 设置为false可禁用与此连接关联的所有模型的自动索引创建。
  - options.bufferCommands=true: 设置为false可禁用与此连接关联的所有模型上的缓冲。
  
Example:
```javascript
var opts = { db: { native_parser: true }}
db = mongoose.createConnection('mongodb://user:pass@localhost:port/database', opts);
```
### Mongoose.prototype.connect()
打开默认的 mongoose 连接，如果连接成功返回一个 Promise。
参数：
- uri: mongodb连接地址
- options
  - options.dbName: 要使用的数据库的名称。如果未提供，默认使用连接字符串中的数据库名称。
  - options.user: 用于身份认证的用户名
  - options.pass: 用于身份认证的密码
  - options.autoIndex=true: Mongoose 特定选项。设置为false可禁用与此连接关联的所有模型的自动索引创建。
  - options.bufferCommands=true: Mongoose 特定选项。设置为false可禁用与此连接关联的所有模型上的缓冲。
  - options.useCreateIndex=true: Mongoose 特定选项。如果为true，则此连接将使用createIndex()而不是ensureIndex()通过Model.init()进行自动索引构建。
  - options.useFindAndModify=true: 设置为false以使findOneAndUpdate()和findOneAndRemove()使用原生findOneAndUpdate()而不是findAndModify()。
  - options.useNewUrlParser=false: 设置为 true,当uri连接中的 db 不存在时自动创建，否则会报错。
- callback(Function

### Mongoose.prototype.disconnect()
回调在所有连接关闭后或第一次发生错误时调用，会并行运行所有连接上的.close()。

参数：

- callback <Function>： 在所有连接关闭后或第一次发生错误时调用。
返回值：

返回一个Promise，在所有连接关闭时返回resolve状态，或在发生第一个错误返回reject状态。

### Mongoose.prototype.connection
Mongoose 模块的默认连接。相当于`mongoose.connections[0]`

Example:
```javascript
var mongoose = require('mongoose');
mongoose.connect(...);
mongoose.connection.on('error', cb);
```
### Mongoose.prototype.connections
包含与此Mongoose实例关联的所有连接的数组。默认情况下，有1个连接。调用 createConnection() 会添加到此数组的连接。

Example:
```
const mongoose = require('mongoose');
mongoose.connections.length; // 1 只有默认连接
mongoose.connections[0] === mongoose.connection; // true

mongoose.createConnection('mongodb://localhost:27017/test');
mongoose.connections.length; // 2 
```
### Mongoose.prototype.STATES
用户连接状态

### Mongoose.prototype.mongo
Mongoose使用的node-mongodb-native驱动程序。


### Mongoose.prototype.Aggregate()//TODO
Mongoose Aggregate 类构造函数 

聚合方法，主要用于处理数据（平均值、求和、分组和排序等），返回计算得出的结果。
### Mongoose.prototype.Error()
错误类构造函数
### Mongoose.prototype.CastError()
类型转换错误类构造函数

参数：
- type: 数据类型名称
- value: 转换失败的值
- path: 发生转换错误的路径
- reason?: 抛出的原始错误


### Mongoose.prototype.Collection()
集合：集合就是一组文档，相当于关系型数据库中的一张表
### Mongoose.prototype.Document()
文档：相当于关系型数据库中的一行数据
### Mongoose.prototype.Schema()
数据模式：可以理解为表结构的定义

定义 Schema：
```javascript
const UserSchema = new Schema({
  name: String,
  age: Number
})
```
### Mongoose.prototype.Query()
Mongoose 查询类构造函数。

### Mongoose.prototype.Model()

模型：由 Schema 生成，可对数据库进行操作

生成 Model：
```javascript
const User = mongoose.model('User', UserSchema)
```

### Mongoose.prototype.deleteModel()
如果存在，移除默认连接中名为 `name` 的模型。你可以使用这个函数清除在测试中创建的任何模型，以防发生 OverwriteModelErrors 错误。

等同于方法 `mongoose.connection.deleteModel(name)`。

参数：
- name：可以是字符串或者正则表达式。如果是字符串，则移除字符串指定名称的模型，如果使用正则表达式会删除所有名称匹配的模型。

Example:
```javascript
mongoose.deleteModel('User');
console.log(mongoose.model('User')); // undefined
```

### Mongoose.prototype.model()
参数：
- name: 模型名称或类扩展模型
- schema?: 使用的模式
- collection?: 集合名称，如果不传此参数，默认使用模型名称
- skipInit?:布尔值，是否跳过模型初始化

返回值：

与name参数相关的模型。如果模型不存在，Mongoose将创建模型。

此方法可用于定义模型或检索模型。

- 在mongoose实例上定义的模型可用于由同一个mongoose实例创建的所有连接。
- 如果使用两个相同名称但不同模式调用mongoose.model()，则会出现OverwriteModelError。
- 如果使用相同的名称和相同的模式调用mongoose.model()，将获得相同的模式。

### Mongoose.prototype.modelNames()
调用此方法返回在此Mongoose实例上创建的模型名称数组。
```javascript
mongoose.model('User', new Schema({ name: String }))
mongoose.modelNames() //['User']
```
### Mongoose.prototype.SchemaType()
基本数据类型构造函数
```javascript
const schema = new Schema({ name: String });
schema.path('name') instanceof SchemaType; // true
```
### Mongoose.prototype.SchemaTypes
mongoose.Schema.Types的别名，用于向后兼容。
### Mongoose.prototype.Types
各种 Mongoose 类型。

Example:
```javascript
var mongoose = require('mongoose');
var array = mongoose.Types.Array;
```
Types:
ObjectId/Buffer/SubDocument/Array/DocumentArray

### Mongoose.prototype.Decimal128
用于在模式中声明为128位十进制浮点的数据类型。
不要使用它来创建新的 Decimal128 实例，而是使用 mongoose.Types.Decimal128。
Example:
```javascript
const vehicleSchema = new Schema({ fuelLevel: mongoose.Decimal128 });
```

### Mongoose.prototype.ObjectId
用于在模式中声明 MongoDB ObjectIds 的数据类型。
不要使用它来创建新的 ObjectId 实例，而是使用 mongoose.Types.ObjectId。

### Mongoose.prototype.Number
数字数据类型。
```javascript
const schema = new Schema({ num: mongoose.Number });
// 等同于
const schema = new Schema({ num: 'number' });
```

### Mongoose.prototype.Mixed
Mixed SchemaType，混合类型，可以是任何类型。
```javascript
const schema = new Schema({ arbitrary: mongoose.Mixed });
```
### Mongoose.prototype.Promise
Mongoose Promise 构造函数
### Mongoose.prototype.PromiseProvider()
mongoose promises 存储层
### Mongoose.prototype.VirtualType()
Mongoose VirtualType类的构造函数。

### Mongoose.prototype.mquery
mquery 查询构造器

### Mongoose.prototype.now()
Mongoose使用此函数来设置时间戳时获取当前时间。你可以使用像Sinon这样的工具来验证这个功能。
```javascript
mongoose.now()//2019-02-16T07:44:50.212Z
```

### Mongoose.prototype.plugin()
声明在所有Schema上执行的全局插件。相当于在你创建的每个Schema上调用.plugin(fn)。
参数：
- fn: 回调函数
- options: 可选项
### Mongoose.prototype.pluralize()
参数可为 `function/null`，传入一个函数时可以重写mongoose的集合名变复数逻辑（自动在用户定义的集合名后加s），如下生成的集合名为 datas。
```javascript
mongoose.model('data', dataSchema);
```
版本5.x以上，可以使用 `mongoose.pluralize(null)` 来禁用变复数逻辑。
[关于变复数问题](https://stackoverflow.com/questions/10547118/why-does-mongoose-always-add-an-s-to-the-end-of-my-collection-name)

### Mongoose.prototype.set()
设置mongoose的选项
```javascript
mongoose.set('debug', true)
```
可支持选项：
- debug: 将mongoose发送到MongoDB的操作打印到控制台。
![image](https://raw.githubusercontent.com/mengQ99/Mongoose-API-Docs/master/images/mongoose-1.png)
- bufferCommands: 启用/禁用所有连接和模型的mongoose缓冲机制。
- useCreateIndex: 默认false。设置为true以使Mongoose的默认索引构建使用createIndex()而不是ensureIndex()来避免MongoDB驱动程序的弃用警告。
- useFindAndModify: 默认true。设置为false以使findOneAndUpdate()和findOneAndRemove()使用本机findOneAndUpdate()而不是findAndModify()。
- useNewUrlParser: 默认false。设置为true以使所有连接默认设置为useNewUrlParser选项。
- cloneSchemas: 默认false。设置为true以使在编译为模型(model)之前克隆(deep copy)所有的模式(schema)。
- applyPluginsToDiscriminators: 默认 false。设置为true则将全局插件应用于鉴别器（Discriminator）模式。通常这是不必要的，因为插件应用于基本模式，并且鉴别器从基础模式复制所有中间件、方法、静态和属性。
- objectIdGetter: 默认true。Mongoose会为MongoDB ObjectId添加一个名为_id的getter，为了方便起见，它会返回this。将其设置为false可以删除getter。
- runValidators: 默认false。设置为true则将为所有验证程序启用更新验证程序。
- toObject
- toJSON
- strict: 默认true。可能为false/true/'throw'。设置模式为默认严格模式。
- selectPopulatedPaths
### Mongoose.prototype.get()
获取mongoose的选项设置
```javascript
mongoose.get('debug') //true
```
### Mongoose.prototype.startSession()
需要MongoDB >= 3.6.0。启动一个MongoDB会话以使操作保持因果一致性、可重写（Retryable Writes）和事务性之类。

调用mongoose.startSession()等于调用mongoose.connection.startSession()。会话的作用域是一个连接，所以调用mongoose.startSession()会在mongoose默认连接上启动一个会话。
### Mongoose.prototype.version
Mongoose 版本。



