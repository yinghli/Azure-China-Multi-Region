# Azure-China-Multi-Region
How to build multi region network

Azure China have four regions. China North(CN), China North 2(CN2), China East(CE) and China East 2(CE2). Those four regions are interconnected by Microsoft backbone network(MSFT). If customer have virtual machine at China East(vmce1) and virtual machine at China East 2(vmce2), vmce1 and vmce2 have below communication method.
1.	Both virtual machines have public IP (PIP), they can direct communicate with their PIP. This is also work for PaaS. The traffic will stay at Microsoft backbone network. 
2.	Setup VPN gateway in each VNET and leverage site-to-site VPN. vmce1 and vmce2 can communicate with dynamic IP (DIP). 
3.	Setup ExpressRoute gateway in each VNET and using ExpressRoute circuit to communicate. vmce1 and vmce2 can communicate with dynamic IP (DIP). 
