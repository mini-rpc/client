# Mini-RPC
simple but effective RPC framework. Both [server](https://github.com/mini-rpc/server) and client.

## Usage

- [Get start](#Get-start)
  - [Install](#install)
  - [Client](#client)

### Get start

#### Install
```sh
npm i @mini-rpc/client
# or
pnpm add @mini-rpc/client
# or
yarn add @mini-rpc/client
```

### Client

```ts
import { RPCClient } from "@mini-rpc/client";

const client = new RPCClient("ws://localhost:3000");
client.connect();

client
  .call("add", [1,2,3])
  .then((result) => {
    console.log(result); // 6
  })
  .catch((err) => {
    console.error(err);
  });
```

### Tips

- the `@Callable` method can be asynchronous.

```ts

class x {
	//...

	@Callable()
	async add(a:number,b:number) {
		// asynchronous code
	}
	
	// or declare the return type Promise

	@Callable()
	promiseAdd(a:number,b:number):Promise<number> {
		return Promise<number>()
	}
}

```
