Trade : 0xe09d65762A409a40e28D0A041cA1Dd4bb288d17c


Trade.getFees(uint256,Trade.BuyingAssetType,address,uint256) (sfi__trade__nft.sol#446-467) performs a multiplication on the result of a division:
	-price = paymentAmt.mul(1000).div((1000 + buyerFeePermille)) (sfi__trade__nft.sol#452)
	-sellerFee = price.mul(sellerFeePermille).div(1000) (sfi__trade__nft.sol#454)
Trade.getFees(uint256,Trade.BuyingAssetType,address,uint256) (sfi__trade__nft.sol#446-467) performs a multiplication on the result of a division:
	-price = paymentAmt.mul(1000).div((1000 + buyerFeePermille)) (sfi__trade__nft.sol#452)
	-royaltyFee = price.mul(royaltyPermille).div(1000) (sfi__trade__nft.sol#464)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#divide-before-multiply

Trade.getFees(uint256,Trade.BuyingAssetType,address,uint256).royaltyPermille (sfi__trade__nft.sol#451) is a local variable never initialized
Trade.getFees(uint256,Trade.BuyingAssetType,address,uint256).tokenCreator (sfi__trade__nft.sol#447) is a local variable never initialized
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#uninitialized-local-variables

Reentrancy in Trade.buyAsset(Trade.Order,Trade.Sign) (sfi__trade__nft.sol#486-496):
	External calls:
	- tradeAsset(order,fee) (sfi__trade__nft.sol#493)
		- transferProxy.erc721safeTransferFrom(IERC721(order.nftAddress),order.seller,order.buyer,order.tokenId) (sfi__trade__nft.sol#472)
		- transferProxy.erc1155safeTransferFrom(IERC1155(order.nftAddress),order.seller,order.buyer,order.tokenId,order.qty,) (sfi__trade__nft.sol#475)
		- transferProxy.erc20safeTransferFrom(IERC20(order.erc20Address),order.buyer,owner,fee.platformFee) (sfi__trade__nft.sol#478)
		- transferProxy.erc20safeTransferFrom(IERC20(order.erc20Address),order.buyer,fee.tokenCreator,fee.royaltyFee) (sfi__trade__nft.sol#481)
		- transferProxy.erc20safeTransferFrom(IERC20(order.erc20Address),order.buyer,order.seller,fee.assetFee) (sfi__trade__nft.sol#483)
	Event emitted after the call(s):
	- BuyAsset(order.seller,order.tokenId,order.qty,msg.sender) (sfi__trade__nft.sol#494)
Reentrancy in Trade.executeBid(Trade.Order,Trade.Sign) (sfi__trade__nft.sol#498-507):
	External calls:
	- tradeAsset(order,fee) (sfi__trade__nft.sol#504)
		- transferProxy.erc721safeTransferFrom(IERC721(order.nftAddress),order.seller,order.buyer,order.tokenId) (sfi__trade__nft.sol#472)
		- transferProxy.erc1155safeTransferFrom(IERC1155(order.nftAddress),order.seller,order.buyer,order.tokenId,order.qty,) (sfi__trade__nft.sol#475)
		- transferProxy.erc20safeTransferFrom(IERC20(order.erc20Address),order.buyer,owner,fee.platformFee) (sfi__trade__nft.sol#478)
		- transferProxy.erc20safeTransferFrom(IERC20(order.erc20Address),order.buyer,fee.tokenCreator,fee.royaltyFee) (sfi__trade__nft.sol#481)
		- transferProxy.erc20safeTransferFrom(IERC20(order.erc20Address),order.buyer,order.seller,fee.assetFee) (sfi__trade__nft.sol#483)
	Event emitted after the call(s):
	- ExecuteBid(msg.sender,order.tokenId,order.qty,order.buyer) (sfi__trade__nft.sol#505)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

SafeMath.mod(uint256,uint256) (sfi__trade__nft.sol#327-330) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

solc-0.8.12 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Parameter Trade.setBuyerServiceFee(uint8)._buyerFee (sfi__trade__nft.sol#413) is not in mixedCase
Parameter Trade.setSellerServiceFee(uint8)._sellerFee (sfi__trade__nft.sol#419) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

buyerServiceFee() should be declared external:
	- Trade.buyerServiceFee() (sfi__trade__nft.sol#405-407)
sellerServiceFee() should be declared external:
	- Trade.sellerServiceFee() (sfi__trade__nft.sol#409-411)
setBuyerServiceFee(uint8) should be declared external:
	- Trade.setBuyerServiceFee(uint8) (sfi__trade__nft.sol#413-417)
setSellerServiceFee(uint8) should be declared external:
	- Trade.setSellerServiceFee(uint8) (sfi__trade__nft.sol#419-423)
transferOwnership(address) should be declared external:
	- Trade.transferOwnership(address) (sfi__trade__nft.sol#425-430)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external
. analyzed (7 contracts with 77 detectors), 15 result(s) found

