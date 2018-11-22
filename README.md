# iOS Json自动生成Model文件（ZZJsonToModel兼容YYModel,MJExtension）

* 纯代码编写，无需安装任何插件，一个方法轻松搞定复杂Json生成Model文件。（兼容[YYModel](https://github.com/ibireme/YYModel),[MJExtension](https://github.com/CoderMJLee/MJExtension)）
* 如果 ZZJsonToModel 为您节约了时间，您的**🌟星星**是我优化项目的动力，谢谢🙏🙏🙏
* 如果您发现了bug，或有新的想法和建议，请及时通知我qq（461818526）。

## 示例：
### json示例：

```json
{
  "author" : {
    "bools" : true,
    "author" : {
      "authors" : {
        "author" : 19.100000000000001
      },
      "author" : "zzz"
    }
  },
  "pages" : 256,
  "book_name" : "Harry Potter",
  "book_info" : [
    {
      "one" : "this is one day"
    },
    {
      "one" : 10,
      "id" : "this is id"
    }
  ]
}
```

生成 YYModel 图：
![生成 YYModel 图](https://upload-images.jianshu.io/upload_images/5173163-f81d1de1e64b9a1d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**注：** 示例的json中，有几点特殊。

* 1.重复的key值`author `。
* 2.特殊key值`id`。
* 3.数组`book_info`中的key值`one`的类型不同。
* 4.类名后缀`+Class`。

处理方法：

* 1.重复的key值生成的类名，从第二个类起，类名前加一个`Z`。
* 2.属性名是系统保留字的，全部大写，因为大写不影响智能提示。
* 3.如果数组中相同层级的key值类型不同，统一转化为`id`类型。
* 4.项目不同.h文件中类名相同会引发报错，类名并不会污染数据，建议加上类名后缀。（随机字符串也可以）


## 使用ZZJsonToModel概要
### 1.下载[ZZJsonToModel](https://github.com/zhangs3721/ZZJsonToModel)并导入项目中。ZZJsonToModel目录：
![ZZJsonToModel 目录](https://upload-images.jianshu.io/upload_images/5173163-ba26e943e5895742.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2.导入头文件 `#import "ZZJsonToModel.h"`，调用此方法

```objectivec

/// 生成 YYModel‘s model 调用方法
+ (BOOL)zz_createYYModelWithJson:(NSDictionary *)json fileName:(NSString *)fileName extensionName:(NSString *)extensionName fileURL:(NSURL *)url error:(Error)error;

/// 生成 MJExtension‘s model 调用方法
+ (BOOL)zz_createMJModelWithJson:(NSDictionary *)json fileName:(NSString *)fileName extensionName:(NSString *)extensionName fileURL:(NSURL *)url error:(Error)error;

```
如图：
![调用主方法](https://upload-images.jianshu.io/upload_images/5173163-207318f547a7f185.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3.导入生成好的model文件

![导入生成好的model文件](https://upload-images.jianshu.io/upload_images/5173163-b095b8d8e90d2926.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.引用.h `#import "TestModel.h"`后，使用YYModel（最好注释掉生成Model的代码）

![引用.h 后，使用YYModel](https://upload-images.jianshu.io/upload_images/5173163-daa4306a7da6c189.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**此时 model 已可用，so easy ，记得点🌟星星，谢谢🙏🙏🙏**


