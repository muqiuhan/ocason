I see no more reason for me to program in ReasonML instead of OCaml, so i'm doing this substitution

## 🗄️ Rejson - A JSON Parser in Reason
## Examples

Read json from string
```reason
let json = {|
{ 
  "user": {
    "active": true,
    "props": {
      "name": "nogw"
    }
  }
} 
|} 

let () = 
  json 
  |> Basic.from_string 
  |> Basic.pp
  |> print_endline

  // (JsonObject
  //    [("user",
  //      (JsonObject
  //         [("active", (JsonBool true));
  //           ("props", 
  //             (JsonObject [("name", (JsonString "nogw"))]))]))])
```

---

Read json from Variants

```reason
open Basic

let json' = JsonObject([("name", JsonString("nogw"))])

let () = {
  json' 
  |> Basic.to_string 
  |> print_endline 
  // { "name": "nogw" }  
}
```

---

Read json from file

```reason 
let () = 
  open_in("test.json")
  |> Basic.from_channel 
  |> Basic.pp
  |> print_endline

  // (JsonObject
  //    [("user",
  //      (JsonObject
  //         [("active", (JsonBool true));
  //           ("props", 
  //             (JsonObject [("name", (JsonString "nogw"))]))]))])

```

---

Write json

```reason
open Basic

let json = JsonObject([("name", JsonString("nogw"))])

let () = {
  let oc = open_out("test.json")
  Basic.to_channel(oc, json) 
}
```

---

A simple example of access to the json key

```reason
let json = {|
{ 
  "user": {
    "active": true,
    "props": {
      "name": "nogw"
    }
  }
} 
|} 

let () = 
  json
  |> Basic.from_string
  |> Basic.Util.key("user") 
  |> Basic.Util.key("props")
  |> Basic.Util.key("name")
  |> Basic.Util.to_string
  |> print_endline // nogw
```