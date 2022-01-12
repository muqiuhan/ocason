# rejson
🗄️ A JSON Parser in Reason

## TODO

- [x] use sedlex
- [x] json -> ast 
- [ ] ast -> json

### received:
```
{
  "user": {
    "active": true,
    "name": "nogw",
    "years": 12,
    "emoji": "😀",
    "interests": ["fruits", "terraria", "functional programming"]
  }
}
```

### expect: 
```ocaml
(JsonObject
   [("user",
     (JsonObject
        [("active", (JsonBool true)); ("name", (JsonString "nogw"));
         ("years", (JsonNumber 12));
         ("emoji", (JsonString "\240\159\152\128"));
         ("interests",
           (JsonArray
              [(JsonString "fruits"); (JsonString "terraria");
               (JsonString "functional programming")]))]))])
```
