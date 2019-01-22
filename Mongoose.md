
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

### Mongoose.prototype.Aggregate()//TODO
Mongoose Aggregate 构造函数 

聚合方法，主要用于处理数据（平均值、求和、分组和排序等），返回计算得出的结果。
### Mongoose.prototype.Error()
错误构造函数
### Mongoose.prototype.CastError()
类型转换错误构造函数

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

### Mongoose.prototype.Model()

模型：由 Schema 生成，可对数据库进行操作

生成 Model：
```javascript
const User = mongoose.model('User', UserSchema)
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

### Mongoose.prototype.ObjectId
用于在模式中声明 MongoDB ObjectIds 的数据类型。
不要使用它来创建新的 ObjectId 实例，而是使用 mongoose.Types.ObjectId。

### Mongoose.prototype.Number
数字数据类型。
```javascript
const schema = new Schema({ num: mongoose.Number });
// Equivalent to:
const schema = new Schema({ num: 'number' });
```
### Mongoose.prototype.Connection()
### Mongoose.prototype.disconnect()
### Mongoose.prototype.connect()
### Mongoose.prototype.connection
### Mongoose.prototype.createConnection()
### Mongoose.prototype.STATES
用户连接状态


### Mongoose.prototype.Mixed
### Mongoose.prototype.DocumentProvider()

### Mongoose.prototype.Promise

### Mongoose.prototype.PromiseProvider()

### Mongoose.prototype.Query()

### Mongoose.prototype.VirtualType()

### Mongoose.prototype.deleteModel()


### Mongoose.prototype.get()




### Mongoose.prototype.mongo

### Mongoose.prototype.mquery

### Mongoose.prototype.now()
Mongoose使用此函数来设置时间戳时获取当前时间。你可以使用像Sinon这样的工具来验证这个功能。

### Mongoose.prototype.plugin()

### Mongoose.prototype.pluralize()

### Mongoose.prototype.set()

### Mongoose.prototype.startSession()

### Mongoose.prototype.version
Mongoose 版本。



