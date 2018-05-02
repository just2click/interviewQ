JavaScript Front End Developer Questions/Tests

 

*1) Closure, setTimeout and scoping*

 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// What will be the following code output?
const arr = [10, 12, 15, 21];
for (var i = 0; i < arr.length; i++) {
    setTimeout(functionn () {
        console.log('Index: ' + i + ', element: ' + arr[i]);
    }, 3000);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Correct Answer:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Index: 4, element: undefined 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

This line would print 4 times (size of array)

 

How would you fix it?

 

Possible solutions:

The easy one:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
const arr = [10, 12, 15, 21];

for (let i = 0; i < arr.length; i++) {
    setTimeout(functionn () {
        console.log('Index: ' + i + ', element: ' + arr[i]);
    }, 3000);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Change the loop counter from var (ES5) to let (ES6) - let will not have the
binding issues

 

Insert the i into the loop

 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
const arr = [10, 12, 15, 21];

for (var i = 0; i < arr.length; i++) {
    setTimeout(function(i_local) {
        return function() {
          console.log('Index: ' + i + ', element: ' + i_local);
        }
    }(i), 3000);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

*2) Currying*

 

Currying is not a native to JavaScript, we will have to write our own

 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// What will be the following code output?

function foo (n) {
	var n = 4;
	return function (t) {
		return n + t;
	}
}

foo(8)(2);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Correct answer:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
6
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

The “trick” here is the fact the “inner” n is used instead of the first value
(8)

 

*3) Casting*

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
null === undefined
null == undefined
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Correct answer:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
false
true
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

*4) Scoping and hoisting*

 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// What will be the following code output?

var a = 1;

function b() {
    a = 10;

    return;

    function a() {};
}

b();

console.log(a);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Correct answer:

 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

This is because the

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
funcation a() {}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

statement has now created **a** local a that has a functional/local scope. This
new **a** now gets hoisted to the top of the enclosing function **b()** with
it’s declaration and definition.

 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// What will be the following code output>

function foo() {
    function bar() {
        return 3;
    }
    return bar();

    function bar() {
        return 8;
    }
}

alert(foo());
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Correct answer:

 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
8
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

This is because: Both **bar()** functions are function declarations and will
therefore be hoisted to the top of **foo()** local scope. However, the **bar()**
returning 8 will be hoisted after the one returning 3. Therefore, the one
returning 8 will be executed.

*5) Short code assignments*

 

a) Design and build (components, basic screens) a website that handles
box-office application:

1.  Set screens

    1.  Registration:

        1.  What fields are needed?

        2.  Validations? Name, email, credit card

    2.  Seat selection

        1.  Should have an array(s) of seats in the theater

        2.  User should see which seats are already taken

        3.  When the user selects a seat/s the selection should be reflected on
            other users screens

        4.  User can deselect a seat before making a purchase - reflect it too
            to other users

    3.  Make a purchase

        1.  Once the user makes a purchase update server and other users

2.  What will you use?

    1.  Components?

    2.  Screens? validations?

    3.  Services?

    4.  State management?

    5.  Updating clients (preferred answer web-sockets)

 

b) ServiceSanta function

Write a function that gets an array of people (names).

The output follow the following rules:

1.  Every person should get a gift from someone (not himself)

    1.  Every person should give a gift to someone (not himself)

 

points to look for:

-   Using a Hash or not

-   What happens if we have the following situation:

    Original array: [’Dror’, Roey’, ‘Jordan’]

    Output:

    Dror - \> Roey

    Roey -\> Dror

    Jordan -\> Jordan???

     

    (The solution that was offered me by the interviewer was to “break the
    chain” - try to switch the one of the existing pairs receiver with the name
    we have left alone. Another point of interest, in order to perform this test
    as fewer times as possible we should check it only for the last pairing)

     

c) Shapes

-   Define a base class of shape

-   Build classes to hold:

    -   Circle

    -   Square

    -   Triangle

-   For each shape you should have common properties (such as: Area, perimeter)

 

d) Show a list of items on the screen

Get an array of objects (some data).

Display it on the screen as a list

Add formatting in needed (see sample object below)

Object:

-   Id: number

    -   Name: string

    -   CreatedAt: Date

 

Add styling if applicable

Add a button to delete a record from the list (display only would suffice)
