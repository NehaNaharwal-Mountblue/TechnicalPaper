# TECHNICAL PAPER

## ES6 

ES6 brings many great features like arrow functions, template strings,class destruction, modules, and more to JavaScript. this features make code more modern and more  readable.
In this paper we are going to cover the basic datatypes and data structures.

## Data Types

 The set of types in the JavaScript language consists of primitive values and objects. ES6 added Symbol as a new primitive type in JavaScript.

 ### 1. Objects

 In contrast to primitive data types, objects can represent multiple or complex values and can change over time. the values can be scalar values or functions, or even arays of other objects.


 ### 2. Number

 The Number object represents numerical date, either integers or floating-point numbers.
     Following is the syntax for creating a number object.
     var val = new Number(number);

 ### 3. Boolean

 The Boolean object represents two values, either "true" or "false". If the value parameter is omitted or is 0, -0, null, false, NaN, undefined, or the empty string (""), the object has an initial value of false.
     Use the following syntax to create a boolean object.
     var val = new Boolean(value);

 ### 4. String

 The String object lets us work with a series of characters; it wraps JavaScript’s string primitive data type with a number of helper methods.

 As JavaScript automatically converts between string primitives and String objects, WE can call any of the helper methods of the String object on a string primitive.
      the following syntax to create a String object.
      var val = new String(string);

 ### 5. Symbol (Primitive value)

 ES6 added Symbol as a new primitive type in JavaScript. Unlike other primitive types such as number, boolean, null,undefined, and string, the symbol type doesn’t have a literal form.
 1. We use global Symbol() function to create any new symbol.
    example:
    let firstSymbol = Symbol('first');
 2. The Symbol() function creates a new unique value each time you call it.
   
 3. The Symbol() function accepts a description as an optional argument. The description argument will make your symbol more descriptive.
   
 4. We can access the symbol’s description property using the toString() method. The console.log() method calls the toString() method of the symbol implicitly.
   
 5. Since symbols are primitive values, we can use the  typeof operator to check whether a variable is a symbol. ES6 extended  typeof to return the symbol string when you pass in a symbol variable. And if we attempt to create a symbol using the new operator, we will get an error.

 #### 5.1 Sharing Symbols

 ES6 provides us with the global symbol registry that allows us to share symbols globally. If we want to create a symbol that will be shared, we use the Symbol.for() method instead of calling the Symbol() function.The Symbol.for() method accepts a single parameter that can be used for symbol’s description.
      Example : 
      let sharing = Symbol.for('sharing');

 The Symbol.for() method first searches for the symbol with the sharing key in the global symbol registry. It returns the existing symbol if there is one. Otherwise, the Symbol.for() method creates a new symbol, registers it to the global symbol registry with the specified key, and returns the symbol.

 Later, if we call the Symbol.for() method using the same key, the Symbol.for() method will return the existing symbol.

 To get the key associated with a symbol, you use the Symbol.keyFor() method and if a symbol that does not exist in the global symbol registry, the System.keyFor() method returns undefined.

 #### 5.2 Symbol Usages

 1. Using symbols as unique values.
 2. Using symbol as the computed property name of an object.



## Data Structures

 ES6 introduces two new data structures: Maps and Sets.

 ### 1. Maps 

 Objects are the primary mechanism for creating unordered key/value-pair data structures, otherwise known as maps.
 
 However, the major drawback with objects-as-maps is the inability to use a non-string value as the key.The Map object is a simple key/value pair. Keys and values in a map may be primitive or objects.
      Following is the syntax for the same.
      new Map([iterable])

 The parameter iterable represents any iterable object whose elements comprise of a key/value pair. Maps are ordered, i.e. they traverse the elements in the order of their insertion.

 #### 1.1 Map Values

 To get the lists of values, we use Values(), which return an iterator.

 #### 1.2 Map Keys

 To get the list of Keys, we use Keys(), which returns an iterator over an keys in the map. To determine if a map has a giben key or not we use has().

 #### 1.3 Map Properties

 1. Map.prototype.size : This property returns the number of key/value pairs in the Map object.

 #### 1.4 Map Methods

 1. Map.prototype.clear() : Removes all key/value pairs from the Map object.
 2. Map.prototype.delete(key) : Removes any value associated to the key and returns the value that Map.prototype.has(key) would have previously returned.Map.prototype.has(key) will return false afterwards.
 3. Map.prototype.entries() : Returns a new Iterator object that contains an array of [key, value] for each element in the Map object in insertion order.
 4. Map.prototype.forEach(callbackFn[, thisArg]) : Calls callbackFn once for each key-value pair present in the Map object, in insertion order. If a thisArg parameter is provided to forEach, it will be used as the ‘this’ value for each callback .
 5. Map.prototype.keys() : Returns a new Iterator object that contains the keys for each element in the Map object in insertion order.
 6. Map.prototype.values() : Returns a new Iterator object that contains an array of [key, value] for each element in the Map object in insertion order.

 #### 1.5 WeakMaps

 WeakMaps take(only)objects as keys. those objects are held weakly, which means if the object itself iS garbage collected the entry in the WeakMap is also removed.

 var m = new WeakMap();
 var x = {id: 1},
     y = {id: 2};

 m.set(x, "foo");

 m.has(x); //true
 m.has(y); //false

WeakMaps do not have a size property or clear() method, nor do they expose any iterator over their keys, values, or entries. So, even if we unset the x reference, which will remove its entry from m upon garbage collection, there is no way to tell.

 ### 2. Sets

 A set is an a collection of unique values(duplicates are ignored). The add() method takes the place of the set() method, and there is no get() method.

 #### 2.1 Set Properties

 1. Set.prototype.size : Returns the number of values in the Set object.
   
 #### 2.2 Set Methods

 1. Set.prototype.add(value) : Appends a new element with the given value to the Set object. Returns the Set object.
 2. Set.prototype.clear() : Removes all the elements from the Set object.
 3. Set.prototype.delete(value) : Removes the element associated to the value.
 4. Set.prototype.entries(): Returns a new Iterator object that contains an array of [value, value] for each element in the Set object, in insertion order. This is kept similar to the Map object, so that each entry has the same value for its key and value here.
 5. Set.prototype.forEach(callbackFn[, thisArg]) : Calls callbackFn once for each value present in the Set object, in insertion order. If athisArg parameter is provided to forEach, it will be used as the ‘this’ value for each callback.
 6. Set.prototype.has(value): Returns a boolean asserting whether an element is present with the given value in the Set object or not.
 7. Set.prototype.values(): Returns a new Iterator object that contains the values for each element in the Set object in insertion order.
   
 #### 2.3 WeakSets
 A WeakSets holds its values weakly(there are no keys). WeakSet Values must be objects, not primitive values as is allowed with sets.

 var s = new WeakSet();

 var x = {id: 1};
     y = {id: 2};

 s.add(x).add(y);

 x = null;     // 'x' is GC-able
 y = null;     //'y' is GC-able

## References 
 
 1. You Don't Know JS: ES6 and Beyond - Kyle Simpson
 2. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures
 3. https://www.freecodecamp.org/news/write-less-do-more-with-javascript-es6-5fd4a8e50ee2/
 4. https://www.javascripttutorial.net/es6/
 5. https://www.tutorialspoint.com/es6/es6_collections.htm
