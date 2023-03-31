`$set`,`$forceUpdate`,`$nextTick`都没用
```js
changeDependentBirthDate(scope){
      var age = this.getDependentAge(scope.row);
      //修改el-table的数据源，不要修改socpe或row
      this.form.dependent[scope.$index].age=age;
      //通过解构赋值触发el-table的重新渲染
      this.form.dependent = [...this.form.dependent];
     }
```