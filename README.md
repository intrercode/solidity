```solidity
pragma solidity ^0.8.4;

contract MyContract {
    mapping(address => uint256) public balances;
    // address payable wallet;

    event Sent(address from, address to, uint amount);

    address public minter;
    
    
    constructor() public {
        minter = msg.sender;
    }


    function mint(address reciver, uint amount) public{
        require(msg.sender == minter);

        balances[reciver] += amount;
    }

    function send(address reciver, uint amount) public {
        balances[msg.sender] -= amount;
        balances[reciver] += amount;
        emit Sent(msg.sender, reciver, amount);
    }
}
```
