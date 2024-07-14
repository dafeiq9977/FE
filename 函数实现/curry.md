```JavaScript
function _callWithPreviousArgs(fn, arguments){
  let args = [].slice.call(arguments, 1)
  return function(){
    return fn.apply(this, args.concat([].slice(arguments)))
  }
}
function curry(fn, length){
  length = length || fn.length
  return function() {
    if(arguments.length < length) {
      return curry(_callWithPreviousArgs.apply(this, [fn, ...([].slice.call(arguments))]), length-arguments.length)
    } else{
      return fn.apply(this, arguments)
    }
  }
}
```
