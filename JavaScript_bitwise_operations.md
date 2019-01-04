# A [bitwise operations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators) in Javascript 

## Bitwise 

|   |   | 
|---|---|
| AND  | A & B  |  
|  OR |  A \| B | 
|  XOR  | A ^ B  | 
|  NOT  | ~ B  |  
|  Shift N position to left  | A << N  | 
|  Shift N position to right  | A >> N  |  
|  Zero-fill right shift  | A >> N  |  

## Do not confuse thme with the [logical operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)

- **&** is not **&&**
- **|** is not **||**
- **!** well, you get the idea ... is not **~**

## Binary to Decimal conversion

In Javascript, you can make bitwise operations on any number but for show a number in binary you need a trick :



```
function convertToBinary(decimalNumber){
	bits =[]
	
	while(decimalNumber > 0){
		if(decimalNumber % 2 == 1) {
			bits.push(1)
		}else{
			bits.push(0)
		}
		decimalNumber = parseInt(decimalNumber / 2)
		
	}
	return bits.join('')
}

convertToBinary(decimalNumber) // Output is "101"
```

But there is also this trick:

```
const x = 5;
const binary = (x).toString(2)

console.log(binary) // Output is "101"
```

And for convert a number to Binary you can use

[ES6 Reference](http://es6-features.org/#BinaryOctalLiteral)

```
(ES6)
0b111110111 === 503
```


```
(ES5)
parseInt("101", 2)
```

## Bonus 
### - An alternative of parseInt:

```
// number | 0  return the integer part of the number or 0 

test = [0,1, 2.3, "string" ,null ,NaN ]

test.forEach(function(element) {
	console.log(`element | 0  =   ${element | 0}`);
});

/*
	element | 0  =   0
	element | 0  =   1
	element | 0  =   2
	element | 0  =   0
	element | 0  =   0
	element | 0  =   0
*/

```

	
