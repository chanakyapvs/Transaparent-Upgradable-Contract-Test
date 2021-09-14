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



