#Stokvel

pragma solidity ^0.6.0;

contract Stokvel {
    // Do stuff
}

contract Stokvel {
    //...
    enum State { AWAITING_PAYMENT, AWAITING_DELIVERY, COMPLETE }
    
    State public currState;
    
    address public buyer;
    address payable public seller;
    //....
}

contract Stokvel {
  
  	//...
  
  constructor(address _buyer, address payable _seller) public {
        buyer = _buyer;
        seller = _seller;
    }
  
  	//...
}

contract Stokvel {
  
  	//...
  
  function deposit() onlyBuyer external payable {
        require(currState == State.AWAITING_PAYMENT, "Already paid");
        currState = State.AWAITING_DELIVERY;
    }
  
  	//...
}

contract Stokvel {
  
  	//...
  
  function confirmDelivery() onlyBuyer external {
        require(currState == State.AWAITING_DELIVERY, "Cannot confirm delivery");
        seller.transfer(address(this).balance);
        currState = State.COMPLETE;
    }
  
  	//...
}

contract Stokvel {
    enum State { AWAITING_PAYMENT, AWAITING_DELIVERY, COMPLETE }
    
    State public currState;
    
    address public buyer;
    address payable public seller;
    
    modifier onlyBuyer() {
        require(msg.sender == buyer, "Only buyer can call this method");
        _;
    }
    
    constructor(address _buyer, address payable _seller) public {
        buyer = _buyer;
        seller = _seller;
    }
    
    function deposit() onlyBuyer external payable {
        require(currState == State.AWAITING_PAYMENT, "Already paid");
        currState = State.AWAITING_DELIVERY;
    }
    
    function confirmDelivery() onlyBuyer external {
        require(currState == State.AWAITING_DELIVERY, "Cannot confirm delivery");
        seller.transfer(address(this).balance);
        currState = State.COMPLETE;
    }
}
