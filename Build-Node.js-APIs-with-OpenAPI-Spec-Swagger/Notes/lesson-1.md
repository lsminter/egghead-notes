I ran through all of the commands just fine until it came to starting the server. The issue I was running into was 

```
Error initializing middleware
Error: Cannot find module '/Users/lucasminter/Desktop/work/egghead-notes/Build-Node.js-APIs-with-OpenAPI-Spec-Swagger/Code/todo-api/api/fittings/swagger_router'
```

Turns out this is a node error. The node version I was on was unstable so I downgraded back to `10.16.0` and then running `swagger project start` worked fine! [Here](https://github.com/swagger-api/swagger-node/issues/586) is some documentation on that. 

