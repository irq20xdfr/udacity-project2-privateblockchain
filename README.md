# Codebase for Private Blockchain for Udacity's Blockchain Developer 2nd Project

Blockchain has the potential to change the way that the world approaches data. Develop Blockchain skills by understanding the data model behind Blockchain by developing your own simplified private blockchain.

## Leveraging ES6 Class features

I used classes and methods to keep the modularity and take advantage of the new Javascript features
Learned from this Udacity courses:

ES6 - JavaScript Improved - [https://www.udacity.com/course/es6-javascript-improved--ud356]
JavaScript Promises - [https://www.udacity.com/course/javascript-promises--ud898]
Object-Oriented JavaScript - [https://www.udacity.com/course/object-oriented-javascript--ud711]

### Using async/await new feature to keep consistency

```let myBlockChain = await factory(Blockchain.Blockchain);```
The factory pattern is used to wait for the Blockchain class object to be ready before using it for adding blocks, preventing this way double Genesis block adding and other unexpected behaviour

### Chaining promises

- As learned in the Udacity JavaScript Promises course, i chained several promises in validateChain method to:

1. Get current validating block data
2. Get next block data to check the previousBlockHash field value and check the links are valid
3. Adding any detect blocks to the array and return it as a result

## Testing

To test code:
1: Uncomment necessary lines from simpleChain.js code, depending of the method that you want to test
2: Uncomment the following part in which 10 blocks are added to the DB, in order to test.
3: Run node simpleChain.js
```
(function theLoop (i) {
		setTimeout(function () {
			let blockTest = new Block.Block("Test Block - " + (i + 1));
			// Be careful this only will work if your method 'addBlock' in the Blockchain.js file return a Promise
			myBlockChain.addBlock(blockTest).then((result) => {
				console.log(result);
				i++;
				if (i < 10) theLoop(i);
			});
		}, 2000);
	  })(0);
```
4: Example of getting a block data
```
	myBlockChain.getBlock(0).then((block) => {
		console.log(JSON.stringify(block));
	}).catch((err) => { console.log(err);});
```
=======

