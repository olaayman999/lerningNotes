``` javascript
const apiKey = generateKey()
const items = await getItemData()

logItems(items)

// don't touch below this line

async function getItemData() {
  const response = await fetch('https://api.boot.dev/v1/courses_rest_api/learn-http/items', {
    method: 'GET',
    mode: 'cors',
    headers: {
      'X-API-Key': apiKey,
      'Content-Type': 'application/json'
    }
  })
  return response.json()
}

function generateKey() {
  const characters = 'ABCDEF0123456789'
  let result = ''
  for (let i = 0; i < 16; i++){
    result += characters.charAt(Math.floor(Math.random() * characters.length))
  }
  return result
}

function logItems(items) {
  for (const item of items) {
    console.log(item.name)
  } 
}

```
this code generates a random API key, uses it to make a GET request to an API endpoint, retrieves and parses the JSON data from the response, and logs the names of the items in the response to the console.



### what is await

await is an operator used in an async function to pause the execution of the function until a Promise is resolved. When await is used on a Promise, it waits for the Promise to be resolved and returns the resolved value.

If the Promise is rejected, await throws an error and can be caught using try...catch blocks.

The await operator can only be used within an async function, and it can be used with any function that returns a Promise, including built-in browser or Node.js APIs, or Promises returned by custom functions.

The use of await allows for more readable and synchronous-looking code, instead of having to work with nested callbacks or using .then() to chain multiple Promises.





