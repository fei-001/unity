## C#学习笔记

//在控制台打印

```Console.WriteLine("你好世界！")
Console.WriteLine("你好世界！")；//在控制台打印后自动空一行

Console.Write("你好世界！")；//在控制台打印后不会自动空行
```

//检测玩家输入的代码

```
Console.ReadLine(“请输入内容”);//输入一行数据才会结束
Console.Readkey();//检测玩家是否按键，只要按了任意键就会结束
```

## 变量

### 1.折叠代码

```
#region  #endregion
```

### 2.声明变量

// 变量类型 变量名 =  初始值；

```
int i = 1 ;
```

### 3.常量

`//关键字 const`

`//固定写法 ：const 变量类型   变量名  = 初始值；`

 例如：

```
const int i=20;
```

##### 特点：

1.必须初始化

2.不能被修改

### 4.强制转换类型

语法：变量类型  变量名 = （变量类型）变量；

### 5.异常捕获

try{

//如果try中的代码报错了不会让程序卡死

}

catch{

//如果出错了，会执行catch中的代码来捕获异常

}

finally{

//最后执行的代码，不管有没有出错，都会执行其中的代码

}

### `6.if`

语法

```
if(bool类型值){
满足条件时，多执行一些代码
}



-----------------
if(bool类型值){
满足条件时，多执行一些代码
}
else
{
     不满足条件执行的代码
}


--------------------
if(bool类型值){
满足条件时，多执行一些代码
}
else if(bool类型值)
{
满足条件执行的代码
}
else
{
     不满足条件执行的代码
}
```

### `7.switch`

语法

```
switch(变量)
{
   case 常量:
   满足条件执行的代码逻辑；
      break;
   case 常量:
   满足条件执行的代码逻辑；
      break;
   case 可以有无数个
   default:
      如果上面case的条件都不满足就会执行default中的代码
      break;
}
```

### `8.while`

语法

```
while(bool类型的值)
{
  //当满足条件时 就会执行while语句块中的内容
}
```

### `9.do while`

语法

```
do
{
   
}while(bool类型的值);
先执行一次再判断
```

### `10.for`

```
for(初始表达式/条件表达式/增量表达式)
{

}
例如
for(int i =0; i< 10; i++)
{
  
}
```

## unity详解

```
void Awake()
{
 // 初始类
}
```

```
void OnEnable()
{
// 依附的gameObject对象每次激活都会被调用
}
```

```
void Start()
{
//第一帧更新之前执行。比Awake晚一点
}
```

```
void FixedUpdate()
{
//用于进行物理（碰撞）更新，每一帧都执行
}
```

```
void Update()
{
//主要用于游戏核心逻辑更新的函数
}
```

```
void LateUpdate()
{
//一般这个更新是用来处理 ，摄像机位置的更新
}
```

```
void OnDisable()
{
//依附的gameObject对象每次失活都会被调用
}
```

```
void OnDestroy()
{
//依附的gameObject对象被删除时执行
}
```

### 重要成员

1.获取依附的GameObject

```
this.gameObject
```

2.获取依附的GameObject位置信息

```
this.transform.position//位置
this.transform.eulerAngles//角度
this.transform.lossyScale//缩放大小
```

3.获取脚本是否激活

```
this.enabled = false;失活
this.enabled = true;激活
```

### 如何得到依附对象上挂载的其他脚本

```
t = this.GetComponent<name>();//获取一个

——————————————————————————————————
//获取多个
List<name> list= new List<name>();
this.GetComponents<name>(list);
____________________________

//获取子对象挂载的脚本(如果没有子对象默认也会找自己身上的)
this.GetComponentInChildren<name>()
this.GetComponentInChildren<name>(true)//激活
this.GetComponentInChildren<name>(false)//失活
————————————————————————————————
//获取父对象挂载的脚本
this.GetComponentInParent<name>();


__________________________________
获取脚本
name lihua;
if(this.TryGetComponent<name>(out lihua))
{
//
}

```

### 成员变量

###### 名字

```
this.gameObject.name
```

######  是否激活

```
this.gameObject.activeSelf
```

###### 是否是静态

```
this.gameObject.isStatic
```

###### 层级

```
this.gameObject.layer
```

###### 标签

```
this.gameObject.tag
```

### gameObject静态方法

创建自带几何体

```
GameObject obj =GameObject.CreatePrimitive(PrimitiveType.Cube);
obj.name="襾餱"
```

查找对象

```
GameObject obj = GameObjece.Find("name");
//通过tag查找
GameObject obj = Gameobject.FindGameObjectWithTag("name");
//通过tag查找多个对象
GameObject[] obj = GameObject.FindGameObjectWithTag("name");

```

###### 找到挂载某一个脚本的对象

```
lesss obj = GameObject.FindObjectOfType<jb>();
```

#### 克隆对象

```
GameObject.Instantiate(obj);
```

#### 删除对象

 ```
 GameObject.Destroy(obj,s);s->延迟几秒
 GameObject.Destroy(this);//删除脚本
 ```

### 成员对象方法

创建空物体

```
GameObject name= new GameObject();
GameObject name= new GameObject("name");//带名字的
GameObject name= new GameObject(“带脚本”，typeof(name));
```

动态添加脚本

```
name.AddComponent<jbname>();
```

设置激活失活

```
name.SetActive(false);
name.SetActive(true);
```

### Time

//用于游戏中参与位移，计时，时间暂停等

 ```
 1.时间比例缩放
 //时间停止
 Time.timeScale=0;
 //回复正常
 Time.timeScale=1;
 //2倍速
 Time.timeScale=2;
 2.帧间隔时间(主要用来计算位移) 
 //路程=时间*速度
 
 游戏暂停就不动的使用`Time.deltaTime`
 不受暂停影响Time.unscaledDeltaTime
 
 物理帧间隔时间 FixedUpdate
 受scale影响
 Time.fixedDeltaTime
 不受scale影响
 Time.fixedUnscaledDeltaTime
 
 ```

## Transform

//游戏对象（GameObject）位移，旋转，缩放，父子关系，坐标转换等相关操作都由它处理

1.Vector3基础

```
Vector3主要是用来表示三维坐标系中的一个点或者一个向量
//申明
Vector3 v = new Vector3();
v.x=10;
v.y=10;
v.z=10;
或者
Vector3 v2 = new Vector(10,10);
```

常用

```
Vector3.zero;//000
Vector3.right;//100
Vector3.left;//-100
Vector3.forward;//001
Vector3.back;//00-1
Vector3.up;//010
Vector3.down;//0-10
```

#### 计算两个点之间的距离的方法

```
Vector3.Distance(v1,v2);
```

### 位置

相对世界坐标系

```      
this.gameObject.transform 
```

   

