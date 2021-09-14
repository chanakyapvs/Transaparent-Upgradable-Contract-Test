# UpgradeSC
Cons:
1. storage locations will not change ie:
proxy contract A 
-> 
(string public name; 
string public email;
function setValue(string memory _string) {
    email = _string;
}) contract B

Now when B is upgraded to :
(string public email; 
string public name;
function setValue(string memory _string) {
    email = _string;
}) contract B

setValue still stores values to storage location 1 on contract A instead of storage location 0
--> Cannot change order of variable and only append variables

2. Collision of function selector (4 byte hash of function name and function signature):

Two functions can have same function selector

Types:
1. Transparent proxy patterns: EIP-1538 : Admins can call only functions for proxy contract but not implementation contract. Helps in not having collision of function selectors
2. Universal upgradable proxis (UUPS): EIP-1822 : Admin only upgrades are in implementation contracts instead of proxy. Compiler itself throws function selector errors. Few less SLOADs for admins on proxy contracts. 
3. Diamond proxies: EIP-2535 : Delegate to multiple implementation contracts.  