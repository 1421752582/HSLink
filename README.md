# @handsometechs/protocol-client


### Installation

	npm i --save @handsometechs/protocol-client


## @handsometechs/protocol-client -> API

### tcp初始化
```javascript
var tcpClient = require('@handsometechs/protocol-client').tcpClient;
var use_tcpClient = new tcpClient(PORT,HOST);

#### wirte(message)
发送数据

*	**message** {string json} required

#### message(callback)
接收数据

*	**callback** {function} required

#### end()
关闭连接

### udp初始化
```javascript
var udpClient = require('@handsometechs/protocol-client').udpClient;
var use_udpClient = new udpClient();

#### wirte(message,port,host)
发送数据

*	**message** {string json} required
*	**port** {string } required
*	**host** {string } required

#### message(callback)
接收数据

*	**callback** {function} required

#### end()
关闭连接

##公有方法

#### DevEUI(param)
接收数据

*	**param** {string} required 8个字节

#### fcnt(number)
接收数据

*	**param** {number} required

#### payload()
接收数据

*	**param** {string} required 16个字节及其倍数

#### DevNonce()
接收数据

*	**param** {string} required 2个字节

#### DevAddr()
接收数据

*	**param** {string} required 4个字节

#### AppKey()
接收数据

*	**param** {string} required 16个字节

#### AppNonce()
接收数据

*	**param** {string} required 2个字节

#### RandomBuffer(param)
接收数据

*	**param** {number} required


## Examples

### tcpClient

```javascript
var tcpClient = require('@handsometechs/protocol-client').tcpClient;
var HOST = 3000;
var PORT = 'localhost';
var use_tcpClient = new tcpClient(PORT,HOST);
var DevEUI = use_tcpClient.RandomBuffer(8);
var DevNonce = use_tcpClient.RandomBuffer(2);
var send = {
    'DevEUI' : DevEUI,
    'DevNonce' : DevNonce
};
use_tcpClient.write(send);
use_tcpClient.message(function (data) {
    console.log('data',data);
})

### udpClient

```javascript
var udpClient = require('@handsometechs/protocol-client').udpClient;
var use_udpClient = new udpClient(PORT,HOST);
var DevEUI = use_tcpClient.RandomBuffer(8);
var DevNonce = use_tcpClient.RandomBuffer(2);
var send = {
    'DevEUI' : DevEUI,
    'DevNonce' : DevNonce
};
var HOST = 3000;
var PORT = 'localhost';
use_udpClient.write(send,PORT,HOST);
use_udpClient.message(function (data) {
    console.log('data',data);
})

