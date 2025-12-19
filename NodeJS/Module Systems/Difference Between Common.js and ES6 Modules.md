## Common JS Modules
- Synchronous file loading
- CJS `require` are not hoisted
- Top level `await` is not allowed
- Only one value can be exported in CJS
- `use strict` mode is not enabled by default
- File extension optional
- If we give full file path the we can load any file using CJS
- It is a convention to add CJS in the file extension
- It is optional to set `"type": "commonjs"` in `package.json` because it is default
- In CJS `this` keyword points to `module.exports` by default

## ES6 Modules
- Asynchronous file loading
- MJS `import` are hoisted
- Top level `await` is allowed
- Multiple value can be exported in MJS
- `use strict` mode is enabled by default
- File extension mandatory
- We can't load any file, only JS and MJS files are allowed
- It is a convention to add MJS in the file extension
- We have to set `"type": "module"` in `package.json`
- In MJS `this` keyword is `undefined`
- In MJS cannot use `__dirname` and `__filename` to get file and directory path. we use `import.meta.filename` and `import.meta.dirname`