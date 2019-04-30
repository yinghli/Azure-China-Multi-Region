## Azure-China-Multi-Region
How to setup traffic flow in Azure China multi region network. 

Azure China have four regions. China North(CN), China North 2(CN2), China East(CE) and China East 2(CE2). Those four regions are interconnected by Microsoft backbone network(MSFT).<br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/Topo.jpg)
If customer have virtual machine at China East(vmce1) and virtual machine at China East 2(vmce2), vmce1 and vmce2 have below communication method. Each virtual machine have public IP(PIP) and dynamic IP(DIP).<br>

# Use virtual machine public IP address
Both virtual machines have PIP, they can direct communicate with their PIP. This is also work for PaaS. The traffic will stay at Microsoft backbone network. Customer need to pay standard ingress and egress charge for this solution. This is same as before.<br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/PIP.jpg)

# Use IPSec VPN
Setup VPN gateway in each VNET and leverage site-to-site VPN. vmce1 and vmce2 can communicate with DIP or private IP. Customer need to pay VPN gateway and VPN gateway egress charge. This is same before. <br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/DIP.jpg)
	
# Use ExpressRoute
Setup ExpressRoute gateway in each VNET and leverage ExpressRoute circuit to communicate. vmce1 and vmce2 can communicate with dynamic IP (DIP). Customer need to pay ExpressRoute Standard circuit charge.<br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/ER.jpg)
Customer already have ExpressRoute Circuit connecting Azure Shanghai PoP location. And already setup private peering.
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/ER1.jpg)
Customer setup ExpressRoute gateway in both CE and CE2 VNET.
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/ER2.jpg)
Customer create ExpressRoute connection from ExpressRoute gateway to same ExpressRoute circuit.
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/ER3.jpg)
From virtual machine effectie route, we can check that two region VNET can be reached via ExpressRoute. vmce1 and vmce2 can communicate with each other with DIP. 
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/ER4.jpg)

# Use Global VNET peering
Global VNET peering is native solution for cross region network communication. It don't need any gateway involved.<br>
Global VNET peering charge is based on ingress and egress. ￥0.1638/GB. 
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/Global.jpg)

```
Note: 
1.  Solution billing is just for reference, this may be changed by product group.
2.  Azure China can't setup global VNET peering to Azure Global.
3.  UDR next hop can't point to Internal load balancer.
```


