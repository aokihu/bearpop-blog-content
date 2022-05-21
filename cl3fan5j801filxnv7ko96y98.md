## Write binray struct like C style in Javascript

Sometimes JavaScript programmers need to parse binary data, or convert JSON objects into binary data and transmit it over the network.

Although there are many third-party libraries that implement JavaScript parsing binary data, these third-party libraries are cumbersome to use. And I find it most difficult to accept that it is impossible to quickly port the structure definitions of the C language to Javascript. 

So I write another library **Quick-Struct**, which is used to easily define **data struct`**from **C** language to **JavaScript**.

It can work on **Node.js**, **Deno** and **Browser**. There is no other dependeic libraries and pure **JavaScript**

You can install **Quick-Struct** from [Quick-Struct NPM](https://www.npmjs.com/package/quick-struct)

# Basic usage

It is very like C language style struct definition. There is an example

```javascript
// Import quick-struct
import {qs} from 'quick-struct'

// This is test binary data
const buffer = new UInt8Array([12]);

// 1. Define struct
const struct = qs`
struct {
  u8 num;
}`

// 2. Parse binary data
const result = struct.decode(buffer).toJson();

console.log(result.num); // Output: 12
```

Now I have defined a struct, it have a field `num`, and the field is `unsigned int` data type. The struct object can parse a byte binary data.

`qs` is string template function, you don't need add bracket with it.

Evenly it is not very usage, and there is more cool thing is **Quick-Struct* can parse **String Type** automatic.