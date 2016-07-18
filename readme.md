<!--
Creator: Alex White
Editor: 
Market: SF, DN
-->
![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Mastering Control Flow

## Why is this important?

*"Control flow" refers to the way our computers move through a program's code. Understanding control flow allows us to trace the flow of a program based on its code. This skill is essential for programming in every language and paradigm. In particular,* **conditionals** *and* **loops** *are fundamental to understanding modern programming languages.*

## What are the objectives?
*After this workshop, developers will be able to:*
- Identify and discuss boolean operators and truthyness
- Use nested `if` statements, ternary operators, and `while` loops
- Use the `break` keyword and `switch` statements.

## Where should we be now?
*Before this workshop, developers should already be able to:*
- create basic `if else` conditionals
- create basic `for` and `while` loops

## Motivator (10 min) 

We're actually starting to write some code that does some real work.

We can even help Santa Claus out.

```javascript
var niceList = [];
var naughtyList = [];
var jimmy = {name: "Jimmy", nice: true, present: "bike"};
var suzy = {name: "Suzy", nice: false};
var kendra = {name: "Kendra", nice: true, present: "xbox"};

var child;
while (niceList + naughtyList) {
	if(niceList){
		child = niceList.pop 
		console.log("Deliver "+ child.name + " " + child.present);
	} else 
	{
		child = naughtyList.pop
		console.log("Leave " + child.name + " a lump of coal");
	}
}
console.log("All presents delivered!"); 
```

Let's run this program and see what happens.

What?!?! What's going on here?

## Thruthiness vs Falsiness (10 min)
*In programming something that* **evaluates** *to True is said to be truthy.*

*Something that* **evaluates** *to False is said to be falsy.*

Most things in JavaScript are *truthy*. In fact,
only the following become false when converted to a Boolean

- `false`
- `0`
- `""` (empty string)
- `NaN`
- `null`
- `undefined`

*Everything else in JavaScript is* **truthy** *!*

You can tell if something is truthy or not by prepending it with `!!` and running it in the console.
Why!?

### Exercise

*What do the following expressions evaluate to in the console?*

`!!1`

`!!"Hello"`

`!!NaN`

`!!undefined`

`!![]`

`!!{}`

[CFU]: # (Try a stop and jot first before trying the console.) 

## `==` vs `===` (10 min)
In JavaScript there are two operators used for comparison, `==` and `===`.
The distinction is simple. Triple-equals checks the *type* while double-equals does not.
Therefor:

```javascript
1 == '1' // returns true but...
1 === '1' // returns false.
```
Question: What should programmers usually use?

### JavaScript Weirdness
Most of this is quite logical. These things work in an intuitive way, as they should.
However, things in JavaScript aren't always so logical...

[WAT?](https://www.destroyallsoftware.com/talks/wat)

## Nested If Statements (15 min)

`if` statements can be nested infinitely!

Example:
```javascript
if(isRaining){
  if(!hasUmbrella){
    if(!hasRainCoat){
      callTaxi();
    };
  };
};
```

That doesn't mean you should nest so deep! More than two layers of `if / else` statement is probably a bad idea.

[CFU]: # (What might be a way to stop nesting if you need lots of logic) 

### Exercise
#### Can I ride?

Jimmy loves roller coasters, but there are a bunch of rules (ugh!) for riding. For starters, it costs 5 tokens. Check the following additional Requirements:
For starters, it costs 5 tokens. Here's how we might code that:

```javascript
var tokens = 3; // Jimmy's tokens

// Can he ride?
if ( tokens >= 5 ) {
    console.log("Step right up!");
} else {
    console.log("Sorry, you can't ride")
}
```

Edit the code above to check the following additional Requirements:

- Must be at least 4ft tall.
- Must be at least 12 years old.
- Replace the previous rule: now riders under 12 must be accompanied by an adult.
- If the boss isn't looking, you can sneak in!
- Riders with a park pass get in free.

Take 6 minutes to work on this. After minute 4, I'll start working on the excercise with my solution.
[Solution](/solution.js)


### Ternary Operator
You can think about the ternary operator as a concise "if-else in one line":
```javascript
isRaining ? callTaxi() : keepWalking();
```

## `while` loops (5 mins) 

![Endless Doughnuts](http://img.pandawhale.com/78624-Homer-Simpson-infinite-donuts-P3EQ.gif)

__While doughnut, eat doughnut!__

In while loops, the initial setup happens before the loop. The continue condition goes inside the parentheses. The update expressions happen inside the loop.

```js
var donuts = 100; // setup:  Here we start with 100 donuts.
while (donuts > 0) { // continue condition: as long as there are still donuts...
  console.log("mmmmm... donut...");
  donuts -= 1; // update: subtract 1 from total
}
```

### The `break` keyword


The break statement terminates the current loop, switch, or label statement and transfers program control to the statement following the terminated statement.

#### Example:
The following function has a break statement that terminates the while loop when i is 3, and then returns the value 3 * x.
```javascript
function testBreak(x) {
  var i = 0;

  while (i < 6) {
    if (i == 3) {
      break;
    }
    i += 1;
  }

  return i * x;
}
```
*-from MDN*

## `switch` statements (5 min)
The switch statement evaluates an expression, matching the expression's value to a case clause, and executes statements associated with that case.

#### Example:

In the following example, if expr evaluates to "Bananas", the program matches the value with case "Bananas" and executes the associated statement. When break is encountered, the program breaks out of switch and executes the statement following switch. If break were omitted, the statement for case "Cherries" would also be executed.
```javascript
switch (expr) {
  case "Oranges":
    console.log("Oranges are $0.59 a pound.");
    break;
  case "Apples":
    console.log("Apples are $0.32 a pound.");
    break;
  case "Bananas":
    console.log("Bananas are $0.48 a pound.");
    break;
  case "Cherries":
    console.log("Cherries are $3.00 a pound.");
    break;
  case "Mangoes":
  case "Papayas":
    console.log("Mangoes and papayas are $2.79 a pound.");
    break;
  default:
    console.log("Sorry, we are out of " + expr + ".");
}

console.log("Is there anything else you'd like?");
```

### Exercise
Refactor the following conditional using a `switch` statement!
```javascript
if(joke.isFunny === 'yes'){
  laugh();
} else if (joke.isFunny === 'sort of'){
  chortle();
} else if (joke.isFunny === 'no'){
  stareBlankly();
};
```
[Solution](/solution.js)

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
