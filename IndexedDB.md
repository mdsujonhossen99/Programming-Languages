- IndexedDB is client side storage
- We can store large volume of data
- It is event/driven and synchronous/asynchronous (non-blocking)
- It is key - Value Pairs
- We can store -
	- Complex objects, Audio, Video, Blobs, Files

**Factors:**
- Open database
- Create object store - like -> SQL -> Table
- Make transactions -> perform operations -> like -> (data add), (retrieval), (removal)

```js
let db;
// for open database
let openRequest = indexedDB.open("DatabaseNameHere", /*version num - optional*/); // this is async task
// listeners
openRequest.addEventListener("success", (e) => {
	console.log("DB Success");
})
openRequest.addEventListener("error", (e) => {
	console.log("DB Error");
})
openRequest.addEventListener("upgradeneeded", (e) => {
	console.log("DB Upgraded");
})
// Output: first -> DB Upgraded, second -> DB Success
// When created database success autometic provided by default version is (1) in database of indexedDB
```