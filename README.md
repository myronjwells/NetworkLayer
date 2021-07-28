# NetworkLayer


This is a personal base Network Layer I created that I use for organizing api calls and endpoints



### Example of Use

- Create a struct or class that will conform to the RequestType protocol that set the protocols ResponseType to a custom Codable JSON structure and data variable with the endpoint details of the api you are trying to call. 
```sh

struct ExampleAccount:Codable {

let objectId: String
let uniqueKey: String?
let firstName: String?
let lastName: String?
}

struct GetExampleAccount: RequestType {
typealias ResponseType = ExampleAccount
var data: RequestData {
return RequestData(path: "https://exampleendpoint.com/accountexample", method: .get, params: nil, headers:nil)
}
}
```

- You can then call this struct or class you created wherever you want mainly best in viewdidload or viewdidappear methods of ViewController. 

```sh 
GetExampleAccount().execute(

onSuccess: { (account: ExampleAccount) in

print(account)
/* will print out account details from json call*/

},
onError: { (error: Error) in error.printDescription()}
)
```


