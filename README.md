# Shibaluv Token

contract deployed [here](https://ropsten.etherscan.io/address/0xc765Cf491ED0321658574e40bC8607B5C27C21FD)

## Notes
- the contract imports ERC20 from @openzeppelin
  - the Shiba Luv Token is an ERC20 token
  - the function mint, uses the _mint function from ERC20 
  - ` function mint(address to, uint256 amount) public onlyRole(MINTER_ROLE) { _mint(to, amount);
    }`

- the contract imports AccessControl from @openzeppelin
  - Information on access control is [here](https://docs.openzeppelin.com/contracts/4.x/api/access#AccessControl)
  - the minter role is given by: `bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");`
    - hash the minter role by using the hash function, keccak256
    - keccak256 returns datatype: bytes32 
    - keccak256 is a one-way crytographic hash function. see [Hashing Functions In Solidity Using Keccak256](https://medium.com/0xcode/hashing-functions-in-solidity-using-keccak256-70779ea55bb0)
    - after creating the MINTER_ROLE, we can use onlyRole(MINTER_ROLE) as a modifier on the mint function to only allow someone with the MINTER_ROLE to mint
    - in the constructor, we also see the granting of two roles. the _grantRole is defined in [access control](https://docs.openzeppelin.com/contracts/4.x/api/access)
      - grantRole(bytes32 role, address account): Grants role to account
    
## Code implementation
- deploy.ts simply deploys the contract and then mints 100 tokens.
- events are emitted [here](https://ropsten.etherscan.io/address/0xc765Cf491ED0321658574e40bC8607B5C27C21FD#events). 
  - grantRole emits a RoleGranted event each time
  - _mint emits a Transfer event
