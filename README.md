# lua-5.4.4-sandbox-escape

### Create docker image

```sh
docker build --tag rce/x64:latest x64
```
### How to run

```sh
docker run -it rce/x64:latest /bin/bash
```

### Exploit

```sh
/LUA/lua/lua /LUA/exploit.lua
```

### Exploit Method

'exploit.lua' uses the use-after-free vulnerability to allow tcache bin poisoning which can change address of the next chunk in tcache bin. Using it, I can allocated a chunk at '__free_hook' and write the address of 'system' function in it. And then, I made some objects which contains 0x68732f6e69622f for containing "/bin/sh". When this script('exploit.lua') is over, 'free(object)' in garbage collecting process becomes 'system("/bin/sh").
