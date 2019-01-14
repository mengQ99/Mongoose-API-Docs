
# Mongoose

### Mongoose()
构造函数 Mongoose
`var mongoose = require('mongoose');`
mongoose 模块的 exports 对象是此类的一个实例。大多数应用只会使用这一个实例。

### Mongoose.prototype.Aggregate()//TODO
Mongoose Aggregate 构造函数 

聚合方法，主要用于处理数据（平均值、求和、分组和排序等），返回计算得出的结果。

### Mongoose.prototype.CastError()

### Mongoose.prototype.Collection()

### Mongoose.prototype.Connection()

### Mongoose.prototype.Decimal128
用于在模式中声明为128位十进制浮点的数据类型。
不要使用它来创建新的 Decimal128 实例，而是使用 mongoose.Types.Decimal128。
Example:
`const vehicleSchema = new Schema({ fuelLevel: mongoose.Decimal128 });`

### Mongoose.prototype.Document()

### Mongoose.prototype.DocumentProvider()

### Mongoose.prototype.Error()

### Mongoose.prototype.Mixed

### Mongoose.prototype.Model()

### Mongoose.prototype.Mongoose()
此方法可以创建另一个 Mongoose 实例。
Example:
`
var mongoose = require('mongoose');
var anotherMongoose = new mongoose.Mongoose();
`

### Mongoose.prototype.Number
数字数据类型。
`
const schema = new Schema({ num: mongoose.Number });
// Equivalent to:
const schema = new Schema({ num: 'number' });
`

### Mongoose.prototype.ObjectId
用于在模式中声明 MongoDB ObjectIds 的数据类型。
不要使用它来创建新的 ObjectId 实例，而是使用 mongoose.Types.ObjectId。

### Mongoose.prototype.Promise

### Mongoose.prototype.PromiseProvider()

### Mongoose.prototype.Query()

### Mongoose.prototype.STATES
用户连接状态

### Mongoose.prototype.Schema()

### Mongoose.prototype.SchemaType()

### Mongoose.prototype.SchemaTypes
mongoose.Schema.Types的别名，用于向后兼容。

### Mongoose.prototype.Types
各种 Mongoose 类型。
Example:
`
var mongoose = require('mongoose');
var array = mongoose.Types.Array;
`
Types:
ObjectId/Buffer/SubDocument/Array/DocumentArray

### Mongoose.prototype.VirtualType()

### Mongoose.prototype.connect()

### Mongoose.prototype.connection

### Mongoose.prototype.createConnection()

### Mongoose.prototype.deleteModel()

### Mongoose.prototype.disconnect()

### Mongoose.prototype.get()

### Mongoose.prototype.model()

### Mongoose.prototype.modelNames()

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



