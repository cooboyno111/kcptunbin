kcptun\_miniexecutable使用方法

基于golang1.8编译，速度比go1.4.2+gomips32编译出来的快一倍。

执行文件体积做到1M。

需要OPENWRT/LEDE平台打开MIPS FPU Emulator。

1在openwrt的SDK目录下，运行命令“make kernel\_menuconfig”, 选择配置“kernel
type”，如下图所示。

![IMG\_256](media/f61cfb529282a8c70c6b9fa48416b526.png)

2、在"kernel type"中，选中"MIPS FPU Emulator"，如下图所示。

![IMG\_257](media/540582b05c70e76be131db0c371639a2.png)

 选择MIPS FPU Emulator

More details please refer to <https://github.com/xtaci/kcptun>

luci-app-kcptun please refer to <https://github.com/kuoruan/luci-app-kcptun>

Sample client config file for MT7620 router with 64M memory.

{

"localaddr": ":12948",

"remoteaddr": "vps:29900",

"key": "it's a secrect",

"crypt": "salsa20",

"mode": "fast",

"conn": 1,

"autoexpire": 300,

"mtu": 1350,

"sndwnd": 128,

"rcvwnd": 256,

"datashard": 10,

"parityshard": 3,

"dscp": 46,

"nocomp": true,

"acknodelay": false,

"nodelay": 0,

"interval": 20,

"resend": 2,

"nc": 1,

"sockbuf": 4194304,

"keepalive": 10

}

Sample server config file for VPS.

{

"listen": ":29900",

"target": "127.0.0.1:12948",

"key": "it's a secrect",

"crypt": "salsa20",

"mode": "fast",

"conn": 1,

"autoexpire": 300,

"mtu": 1350,

"sndwnd": 256,

"rcvwnd": 256,

"datashard": 10,

"parityshard": 3,

"dscp": 46,

"nocomp": true,

"acknodelay": false,

"nodelay": 0,

"interval": 20,

"resend": 2,

"nc": 1,

"sockbuf": 4194304,

"keepalive": 10

}
