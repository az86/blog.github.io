## udp socket 10054

### 在接收端没有启动的情况下
 1.直接ReceiveFrom没问题。
 2.如果先SendTo再ReceiveFrom，SendTo可以正常过，但是RecieveFrom会抛异常，错误码：10054。

### google 到如下信息：这是微软的bug，通过如下代码解决
            var sioUdpConnectionReset = -1744830452;
            var inValue = new byte[] { 0 };
            var outValue = new byte[] { 0 };
            socket.IOControl(sioUdpConnectionReset, inValue, outValue);

### 如果这里有错误，欢迎发送email到 m_sunqi@qq.com。

#### I'm az.