---
title: "utils"
excerpt: "A collection of small utility functions useful during load testing with k6. "
---

The `utils` module contains number of small utility functions useful in every day load testing. 

> ⭐️ Source code available on [GitHub](https://github.com/k6io/k6-jslib-utils). 
> Please request features and report bugs through [GitHub issues](https://github.com/k6io/k6-jslib-utils/issues).





| Function | Description |
| -------- | ----------- |
| [randomIntBetween(min, max)](/javascript-api/jslib/utils/randomintbetween-min-max)  | Random integer in a given range |
| [randomItem(array)](/javascript-api/jslib/utils/randomitem-array)  | Random item from a given array |
| [randomString(length)](/javascript-api/jslib/utils/randomstring-length)  | Random string of a given length |
| [uuidv4()](/javascript-api/jslib/utils/uuidv4)  | Random UUID v4 in a string representation |



## Simple example

<CodeGroup labels={[]}>

```javascript
import { sleep } from 'k6';
import http from 'k6/http';

import { randomIntBetween, 
         randomString,
         randomItem,
         uuidv4 } from "./src/utils.js";

export default function() {

  let res = http.post(`https://test-api.k6.io/user/register/`, {
    first_name: randomItem(['Joe', 'Jane']), // random name
    last_name: 'Smith',
    username: `user_${randomString(10)}@example.com`,  // random email address,
    password: uuidv4() // random password in form of uuid
  });

  sleep(randomIntBetween(1, 5)); // sleep between 1 and 5 seconds.
}
```

</CodeGroup>
