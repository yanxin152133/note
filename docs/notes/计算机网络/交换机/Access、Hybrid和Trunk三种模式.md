# 1. Access、Hybrid和Trunk三种模式
- Access类型的端口只能属于1个VLAN，一般用于连接计算机的端口；
- Trunk类型的端口可以允许多个VLAN通过，可以接收和发送多个VLAN的报文，一般用于交换机之间连接的端口；
- Hybrid类型的端口可以允许多个VLAN通过，可以接收和发送多个VLAN的报文，可以用于交换机之间连接，也可以用于连接用户的计算机。

Hybrid端口和Trunk端口在接收数据时，处理方法是一样的，唯一不同之处在于发送数据时：Hybrid端口可以允许多个VLAN的报文发送时不打标签，而Trunk端口只允许缺省VLAN的报文发送时不打标签。
            
## 1.1. 缺省VLAN
- Access端口只属于1个VLAN，所以它的缺省VLAN就是它所在的VLAN，不用设置；
- Hybrid端口和Trunk端口属于多个VLAN，所以需要设置缺省VLAN ID。缺省情况下，Hybrid端口和Trunk端口的缺省VLAN为VLAN 1。如果设置了端口的缺省VLAN ID，当端口接收到不带VLAN Tag的报文后，则将报文转发到属于缺省VLAN的端口；当端口发送带有VLAN Tag的报文时，如果该报文的VLAN ID与端口缺省的VLAN ID相同，则系统将去掉报文的VLAN Tag，然后再发送该报文。
        
## 1.2. 交换机接口出入数据处理过程
+ Acess端口
  - 收报文
    - 收到一个报文，判断是否有VLAN信息，如果没有则打上端口的VLAN ID，并进行交换转发，如果有则直接丢弃（缺省）。
  - 发报文
    - 将报文的VLAN信息剥离，直接发送出去。
+ trunk端口
  - 收报文
    - 收到一个报文，判断是否有VLAN信息，如果没有则打上端口的VLAN ID，并进行交换转发，如果有判断该trunk端口是否允许该VLAN的数据进入，允许则转发，否则丢弃。
  - 发报文
    - 比较端口的VLAN ID和将要发送报文的VLAN信息，如果两者相等则剥离VLAN信息，再发送，如果不相等则直接发送。
+ hybrid端口
  - 收报文
    - 收到一个报文，判断是否有VLAN信息，如果没有则打上端口的VLAN ID，并进行交换转发，如果有则判断该hybrid端口是否允许该VLAN的数据进入，允许则转发，否则丢弃（此时端口上的untag配置是不用考虑的，untag配置只对发送报文时起作用）。
  - 发报文
    - 判断该VLAN在本端口的属性（disp interface 即可看到该端口对哪些VLAN是untag， 哪些VLAN是tag），如果是untag则剥离VLAN信息，再发送，是tag则直接发送。