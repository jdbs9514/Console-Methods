# Console
The console object provides access to the debugging console (e.g., the Web console in Firefox). The specifics of how it works vary from browser to browser or server runtimes (Node.js, for example), but there is a de facto set of features that are typically provided.

The console object can be accessed from any global object. Window on browsing scopes and WorkerGlobalScope as specific variants in workers via the property console. It's exposed as Window.console, and can be referenced as console. For example:

```javascript
console.log("Failed to open the specified link");
```

# console: log() static method

The **console.log()** static method outputs a message to the console. The message may be a single string (with optional substitution values), or it may be any one or more JavaScript objects.

```javascript
log(obj1)
log(obj1, /* …, */ objN)
log(msg)
log(msg, subst1, /* …, */ substN)
```

## Parameters

**obj1** … **objN**

- A list of JavaScript objects to output. Objects are output in the order listed. Please be warned that if you log objects in the latest versions of Chrome and Firefox, what you get logged on the console is a reference to the object, which is not necessarily the 'value' of the object at the moment in time you call console.log(), but it is the value of the object at the moment you open the console.

**msg**

- A JavaScript string containing zero or more substitution strings.

**subst1** … **substN**

- JavaScript objects with which to replace substitution strings within msg. This gives you additional control over the format of the output.

- See Outputting text to the console in the documentation of console for details.

__Return value__

None (undefined).

# console: warn() static method

The **console.warn()** static method outputs a warning message to the console.

```javascript
warn(obj1)
warn(obj1, /* …, */ objN)
warn(msg)
warn(msg, subst1, /* …, */ substN)
```

## Parameters

**obj1** … **objN**

- A list of JavaScript objects to output. The string representations of each of these objects are appended together in the order listed and output to the console.

**msg**

- A JavaScript string containing zero or more substitution strings, which are replaced with subst1 through substN in consecutive order.

**subst1** … **substN**

- JavaScript objects with which to replace substitution strings within msg. This gives you additional control over the format of the output. See Using string substitutions for a description of how substitutions work.

- See Outputting text to the console in the documentation of the console object for details.

__Return value__

None (undefined).

# console: error() static method

The **console.error()** static method outputs an error message to the console.

```javascript
error(obj1)
error(obj1, /* …, */ objN)
error(msg)
error(msg, subst1, /* …, */ substN)
```

## Parameters

**obj1** … **objN**

- A list of JavaScript objects to output. The string representations of each of these objects are appended together in the order listed and output to the console.

**msg**

- A JavaScript string containing zero or more substitution strings, which are replaced with subst1 through substN in consecutive order.

**subst1** … **substN**

- JavaScript objects with which to replace substitution strings within msg. This gives you additional control over the format of the output. See Using string substitutions for a description of how substitutions work.

- See Outputting text to the console in the documentation of the console object for details.

__Return value__

None (undefined).

# console: info() static method

The **console.info()** static method outputs an informational message to the console. In Firefox, a small "i" icon is displayed next to these items in the console's log.

```javascript
info(obj1)
info(obj1, /* …, */ objN)
info(msg)
info(msg, subst1, /* …, */ substN)
```

## Parameters

**obj1** … **objN**

- A list of JavaScript objects to output. The string representations of each of these objects are appended together in the order listed and output to the console.

**msg**

- A JavaScript string containing zero or more substitution strings, which are replaced with subst1 through substN in consecutive order.

**subst1** … **substN**

- JavaScript objects with which to replace substitution strings within msg. This gives you additional control over the format of the output. See Using string substitutions for a description of how substitutions work.

- See Outputting text to the console in the documentation of the console object for details.

__Return value__

None (undefined).

# console: assert() static method

The **console.assert()** static method writes an error message to the console if the assertion is false. If the assertion is true, nothing happens.

```javascript
assert(assertion)

assert(assertion, obj1)
assert(assertion, obj1, obj2)
assert(assertion, obj1, obj2, /* …, */ objN)

assert(assertion, msg)
assert(assertion, msg, subst1)
assert(assertion, msg, subst1, /* …, */ substN)
```

## Parameters

**assertion**

- Any boolean expression. If the assertion is false, a generic message indicating assertion failure is written to the console.

**obj1** … **objN**

- A list of JavaScript objects to output. A representation of each of these objects is output to the console after a generic assertion failure message (which may be different from the message output when these objects are not present) in the order given with some type of separation between the message and between each of them. There is a special case if obj1 is a string, which is described subsequently.

**msg**

- A JavaScript string containing zero or more substitution strings, which are replaced with subst1 through substN in consecutive order up to the number of substitution strings. A colon, a space, and then the substituted string are appended to the generic assertion message to form a detailed assertion message, and the result is output to the console.

**subst1** … **substN**

- JavaScript objects with which to replace substitution strings within msg. This gives you additional control over the format of the output. See Using string substitutions for a description of how substitutions work. If there are more substutition objects than there are substitution strings, the extra objects are themselves written to the console after the detailed assertion message in the same manner as described for objects written after a generic assertion message.

__Return value__

None (undefined).

# console: clear() static method

The **console.clear()** static method clears the console if the console allows it. A graphical console, like those running on browsers, will allow it; a console displaying on the terminal, like the one running on Node, will not support it, and will have no effect (and no error).

```javascript
clear()
```

## Parameters

None.

__Return value__

None (undefined).

# console: dir() static method

The **console.dir()** static method displays an interactive list of the properties of the specified JavaScript object. The output is presented as a hierarchical listing with disclosure triangles that let you see the contents of child objects.

In other words, **console.dir()** is the way to see all the properties of a specified JavaScript object in console by which the developer can easily get the properties of the object.

![](/image/console-dir.png)

```javascript
dir(object)
```

## Parameters

**object**

- A JavaScript object whose properties should be output.

__Return value__

None (undefined).

# console: group() static method

The **console.group()** static method creates a new inline group in the Web console log, causing any subsequent console messages to be indented by an additional level, until **console.groupEnd()** is called.

```javascript
group()
group(label)
```

## Parameters
**label** (Optional)

- Label for the group.

__Return value__

None (undefined).

## Examples

You can use nested groups to help organize your output by visually associating related messages. To create a new nested block, call **console.group()**. The **console.groupCollapsed()** method is similar, but the new block is collapsed and requires clicking a disclosure button to read it.

To exit the current group, call **console.groupEnd()**. For example, given this code:

```javascript
console.log("This is the outer level");
console.group();
console.log("Level 2");
console.group();
console.log("Level 3");
console.warn("More of level 3");
console.groupEnd();
console.log("Back to level 2");
console.groupEnd();
console.log("Back to the outer level");
```

The output looks like this:

![](/image/nesting.png)

# console: count() static method

The **console.count()** static method logs the number of times that this particular call to **count()** has been called.

```javascript
count()
count(label)
```

## Parameters

**label** (Optional)

- A string. If supplied, **count()** outputs the number of times it has been called with that label. If omitted, **count()** behaves as though it was called with the "default" label.

__Return value__

None (undefined).

## Examples

For example, given code like this:

```javascript
let user = "";

function greet() {
  console.count();
  return `hi ${user}`;
}

user = "bob";
greet();
user = "alice";
greet();
greet();
console.count();
```

Console output will look something like this:

````
"default: 1"
"default: 2"
"default: 3"
"default: 4"
````

The label is displayed as default because no explicit label was supplied.

If we pass the user variable as the label argument to the first invocation of **console.count()**, and the string "alice" to the second:

```javascript
let user = "";

function greet() {
  console.count(user);
  return `hi ${user}`;
}

user = "bob";
greet();
user = "alice";
greet();
greet();
console.count("alice");
```

We will see output like this:

````
"bob: 1"
"alice: 1"
"alice: 2"
"alice: 3"
````

We're now maintaining separate counts based only on the value of label.

# console: time() static method

The **console.time()** static method starts a timer you can use to track how long an operation takes. You give each timer a unique name, and may have up to 10,000 timers running on a given page. When you call **console.timeEnd()** with the same name, the browser will output the time, in milliseconds, that elapsed since the timer was started.

See Timers in the console documentation for details and examples.

```javascript
time()
time(label)
```

## Parameters

**label** (Optional)

A string representing the name to give the new timer. This will identify the timer; use the same name when calling **console.timeEnd()** to stop the timer and get the time output to the console. If omitted, the label "default" is used.

__Return value__

None (undefined).

# console: table() static method

The **console.table()** static method displays tabular data as a table.

This function takes one mandatory argument data, which must be an array or an object, and one additional optional parameter columns.

It logs data as a table. Each element in the array (or enumerable property if data is an object) will be a row in the table.

The first column in the table will be labeled (index). If data is an array, then its values will be the array indices. If data is an object, then its values will be the property names. Note that (in Firefox) console.table is limited to displaying 1000 rows (first row is the labeled index).

## Collections of primitive types

The data argument may be an array or an object.

```javascript
// an array of strings

console.table(["apples", "oranges", "bananas"]);
```
