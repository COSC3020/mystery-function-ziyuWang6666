[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11841663&assignment_repo_type=AssignmentRepo)
# Mystery Function

What does the `mystery()` function in the following piece of code do? Add your
answer to this markdown file.

```javascript
function mystery(a) {
    if(a.length == 1) return a[0];
    var foo = mystery(a.slice(1, a.length))
    if(foo > a[0]) return foo;
    else return a[0];
}
```

## Answer
Function mystery will return the largest element in the a.

if a = [9,5,2,8]; mystery function will return 9

if a = ["z","x","y"]; mystery function will return z.

## explain

When a = [9,5,2,8], **a.length** is 4, will not return a[0]=9.

Every time call a.slice(1, a.length) is to cut off the first element of the array and leave the rest of the array. Every time call the mystery function to create a stack to put a's items.

**a.slice(1,4)** will get [5,2,8];

var foo = mystery([5,2,8]); **call mystery function again**, since a = [5,2,8], a.length != 1, so it goes to mystery([2,8]). Then it continue this way until a = [8], foo = 8, a[0] callback the stack to get a[0]=2.

If foo > a[0], return foo, else return a[0]. foo=8 > a[0]=2 return foo=8.
Then callback stack again to get a[0]=5, foo=8>a[0]=5, return foo=8.
Again callback stack a[0]= 9, foo=8, 9>8, return a[0]=9.
Then because of foo < a[0], so return a[0] = 5;

//get help from Ta: Ali

//I didn't think about every time the calling mystery function actually does not return foo at once. It has something callback the previous stack to get a[0] to compare.
