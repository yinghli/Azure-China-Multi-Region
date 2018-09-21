# Azure-China-Multi-Region
How to setup traffic flow in Azure China multi region network. 

Azure China have four regions. China North(CN), China North 2(CN2), China East(CE) and China East 2(CE2). Those four regions are interconnected by Microsoft backbone network(MSFT).<br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/Topo.jpg)
If customer have virtual machine at China East(vmce1) and virtual machine at China East 2(vmce2), vmce1 and vmce2 have below communication method. Each virtual machine will have public IP(PIP) and dynamic IP(DIP).<br>
1.	Both virtual machines have PIP, they can direct communicate with their PIP. This is also work for PaaS. The traffic will stay at Microsoft backbone network. Customer need to pay standard ingress and egress charge for this solution.<br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/PIP.jpg)
2.	Setup VPN gateway in each VNET and leverage site-to-site VPN. vmce1 and vmce2 can communicate with DIP or private IP. Customer need to pay VPN gateway and VPN gateway egress charge.<br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/DIP.jpg)
3.	Setup ExpressRoute gateway in each VNET and using ExpressRoute circuit to communicate. vmce1 and vmce2 can communicate with dynamic IP (DIP). Customer need to pay ExpressRoute circuit charge.<br>
![](https://github.com/yinghli/Azure-China-Multi-Region/blob/master/ER.jpg)
```
Note: 
1.	Global VNET peering is NOT available at Azure China yet.
2.	Solution billing is just for reference, this may be changed by product group.
3.	Different region network resource can’t setup UDR to point each other.
```


