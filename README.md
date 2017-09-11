# stack
A stack is an ordered collection of items that follows the LIFO (short for Last In First Out) principle.
## Creating a stack
```javascript
function Stack() {
    var items = [];
    this.push = function (element){// This adds a new item (or several items) to the top of the stack
        items.push(element);
    }
    this.pop = function (){
        return items.pop();
    }
    this.peek = function (){// This returns the top element from the stack
        return items[items.length - 1];
    }
    this.isEmpty = function (){// This returns true if stack does not contain any elements.
        return items.length === 0;
    }
    this.size = function (){
        return items.length;
    }
    this.clear = function (){
        items = [];
    }
    this.print = function (){
        console.log(`[${items.toString()}]`);
    }
    this.get = function (){// This gets the whole arry
        return items;
    }
}
```
## Decimal to Binary
```javascript
function divideBy2 (decNumber){
    var remStack = new Stack (),
        rem,
        binaryString = '';
    
    while (decNumber > 0){
        rem = Math.floor(decNumber % 2);
        remStack.push(rem);
        decNumber = Math.floor( decNumber / 2 );
        console.log(decNumber + ' rem = '+ rem);
    }
    remStack.print();
    /*
    while (!remStack.isEmpty()){
        binaryString += remStack.pop().toString();
    }
    
    return binaryString;
    */
    return remStack.get().reverse().join("");
}
console.log(divideBy2(10));
/*
Result:
5 rem = 0
2 rem = 1
1 rem = 0
0 rem = 1
[0,1,0,1]
1010
*/
```
## Decimal to Any Base
```javascript
function baseConverter (decNumber, base){
    var remStack = new Stack(),
        rem,
        baseString = '',
        digits = '0123456789ABCDEF';
    
    while(decNumber > 0) {
        rem = Math.floor(decNumber % base);
        remStack.push(rem);
        console.log(decNumber + ' rem = '+ rem);
        decNumber = Math.floor(decNumber/base);      
    }
    /*
    while(!remStack.isEmpty()){
        baseString += digits[remStack.pop()];//String indexes are zero-based: first character is in position 0
    }
    
    return baseString;
    */
    return remStack.get().map(function(x){return digits[x]}).reverse().join("");
}

console.log(baseConverter (100345 , 16))
/*
Result:
100345 rem = 9
6271 rem = 15
391 rem = 7
24 rem = 8
1 rem = 1
187F9
*/
```
