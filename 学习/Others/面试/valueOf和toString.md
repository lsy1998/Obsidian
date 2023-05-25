console.log()直接打印的话中除了object直接打印、date执行两次toString,其余都toString再用valueOf,
alert(),String()中都只使用了toString()，
如果需要进行运算，都是先进行valueOf再toString
总而言之，**与数字、运算有关的用valueOf优先,其他都是toString优先**
