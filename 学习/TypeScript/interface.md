
#面向对象 
接口用来定义一个类的结构，或者用作类型声明
```ts
interface myInterface{
	name:string;
	age:int;
	sayHello(name:string):void;
}
```
同名interface会合并，而type不会
```ts
interface myInterface{
	name:string;
	age:int;
}
interface myInterface{
	gender:boolean
}

等于
interface myInterface{
	name:string;
	age:int;
	gender:boolean;
}

```
接口中的属性不能有实际的值