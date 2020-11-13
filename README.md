# yGift
Smart contract used to offer gifts to yearn community members for their work in the ecosystem.
yGift is an erc-721 standard based NFT with functionalities to hold erc-20 tokens and attach string messages to a giftt via events.

# Interface

4 events on top of the NFT events:
- 	`event GiftMinted(address indexed from, address indexed to, uint256 indexed tokenId);`
    Triggered when a new gift is minted, allows easy filtering when trying to find the creator, receiver or the specific gift created.
    
-   `event Tip(address indexed tipper, uint256 indexed tokenId, address token, uint256 amount, string message);`
    Triggered when an amount of tokens is tipped in the gift. A broadcast message is also sent in the event which can be tracked easily.
    
-   `event Redeemed(uint256 indexed tokenId);`
    Triggered when the gift receiver "opens" the gift. From that moment on, tokens inside the gift can be redeemed without restrictions.
    
-   `event Collected(address indexed redeemer, uint256 indexed tokenId, address token, uint256 amount);`
    Triggered when the gift owner, withdraws some tokens from the gift.
    
3 public functions:
-   `function tip(uint256 _tokenId, uint256 _amount, string memory _msg) public;`
    Called to send some tokens to a gift. One gift can allow only one token to be tipped. If the gift has been minted with 1000 yUSD inside, you can only tip yUSD.

-   `function redeem(uint256 _tokenId) public;`
    Called by the gift receiver to "open" the gift and receive it to his address. From that moment on, tokens inside the gift can be redeemed without restrictions.
    
-   `function collect(uint256 _amount, uint256 _tokenId) public;`
    Called by the gift owner to withdraw some tokens from the gift.

