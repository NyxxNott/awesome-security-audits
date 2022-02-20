- ERC721 : 0x2bf3a72ce029412F24145238F8cedFE5D46E0354
- ERC1155 : 0x8704F5D561C5Da161A77297fd0A9a156ed427793
- TransferProxy : 0x2de55A5e7C97A7D810e1e0e90B2c6DA6188479eE
- Trade : 0xe09d65762A409a40e28D0A041cA1Dd4bb288d17c


Reentrancy in collectibleds.createCollectible(string,uint256,collectibleds.Sign) (sfi__ERC721.sol#907-916):
	External calls:
	- _safeMint(msg.sender,newItemId,fee) (sfi__ERC721.sol#912)
		- returndata = to.functionCall(abi.encodeWithSelector(IERC721Receiver(to).onERC721Received.selector,_msgSender(),from,tokenId,_data),ERC721: transfer to non ERC721Receiver implementer) (sfi__ERC721.sol#843-849)
		- (success,returndata) = target.call{value: value}(data) (sfi__ERC721.sol#305)
	External calls sending eth:
	- _safeMint(msg.sender,newItemId,fee) (sfi__ERC721.sol#912)
		- (success,returndata) = target.call{value: value}(data) (sfi__ERC721.sol#305)
	State variables written after the call(s):
	- tokenCounter = tokenCounter + 1 (sfi__ERC721.sol#914)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities

ERC721._mint(address,uint256,uint256) (sfi__ERC721.sol#760-774) ignores return value by _holderTokens[to].add(tokenId) (sfi__ERC721.sol#766)
ERC721._mint(address,uint256,uint256) (sfi__ERC721.sol#760-774) ignores return value by _tokenOwners.set(tokenId,to) (sfi__ERC721.sol#768)
ERC721._burn(uint256) (sfi__ERC721.sol#784-801) ignores return value by _holderTokens[owner].remove(tokenId) (sfi__ERC721.sol#796)
ERC721._burn(uint256) (sfi__ERC721.sol#784-801) ignores return value by _tokenOwners.remove(tokenId) (sfi__ERC721.sol#798)
ERC721._transfer(address,address,uint256) (sfi__ERC721.sol#803-817) ignores return value by _holderTokens[from].remove(tokenId) (sfi__ERC721.sol#811)
ERC721._transfer(address,address,uint256) (sfi__ERC721.sol#803-817) ignores return value by _holderTokens[to].add(tokenId) (sfi__ERC721.sol#812)
ERC721._transfer(address,address,uint256) (sfi__ERC721.sol#803-817) ignores return value by _tokenOwners.set(tokenId,to) (sfi__ERC721.sol#814)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#unused-return

collectibleds.constructor(string,string).name (sfi__ERC721.sol#876) shadows:
	- ERC721.name() (sfi__ERC721.sol#615-617) (function)
	- IERC721Metadata.name() (sfi__ERC721.sol#520) (function)
collectibleds.constructor(string,string).symbol (sfi__ERC721.sol#876) shadows:
	- ERC721.symbol() (sfi__ERC721.sol#619-621) (function)
	- IERC721Metadata.symbol() (sfi__ERC721.sol#522) (function)
collectibleds.verifySign(string,address,collectibleds.Sign).tokenURI (sfi__ERC721.sol#893) shadows:
	- ERC721.tokenURI(uint256) (sfi__ERC721.sol#623-636) (function)
	- IERC721Metadata.tokenURI(uint256) (sfi__ERC721.sol#524) (function)
collectibleds.createCollectible(string,uint256,collectibleds.Sign).tokenURI (sfi__ERC721.sol#907) shadows:
	- ERC721.tokenURI(uint256) (sfi__ERC721.sol#623-636) (function)
	- IERC721Metadata.tokenURI(uint256) (sfi__ERC721.sol#524) (function)
collectibleds.setBaseURI(string)._baseURI (sfi__ERC721.sol#918) shadows:
	- ERC721._baseURI (sfi__ERC721.sol#577) (state variable)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#local-variable-shadowing

Reentrancy in collectibleds.createCollectible(string,uint256,collectibleds.Sign) (sfi__ERC721.sol#907-916):
	External calls:
	- _safeMint(msg.sender,newItemId,fee) (sfi__ERC721.sol#912)
		- returndata = to.functionCall(abi.encodeWithSelector(IERC721Receiver(to).onERC721Received.selector,_msgSender(),from,tokenId,_data),ERC721: transfer to non ERC721Receiver implementer) (sfi__ERC721.sol#843-849)
		- (success,returndata) = target.call{value: value}(data) (sfi__ERC721.sol#305)
	External calls sending eth:
	- _safeMint(msg.sender,newItemId,fee) (sfi__ERC721.sol#912)
		- (success,returndata) = target.call{value: value}(data) (sfi__ERC721.sol#305)
	State variables written after the call(s):
	- _setTokenURI(newItemId,tokenURI) (sfi__ERC721.sol#913)
		- _tokenURIs[tokenId] = _tokenURI (sfi__ERC721.sol#828)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2

Reentrancy in collectibleds.createCollectible(string,uint256,collectibleds.Sign) (sfi__ERC721.sol#907-916):
	External calls:
	- _safeMint(msg.sender,newItemId,fee) (sfi__ERC721.sol#912)
		- returndata = to.functionCall(abi.encodeWithSelector(IERC721Receiver(to).onERC721Received.selector,_msgSender(),from,tokenId,_data),ERC721: transfer to non ERC721Receiver implementer) (sfi__ERC721.sol#843-849)
		- (success,returndata) = target.call{value: value}(data) (sfi__ERC721.sol#305)
	External calls sending eth:
	- _safeMint(msg.sender,newItemId,fee) (sfi__ERC721.sol#912)
		- (success,returndata) = target.call{value: value}(data) (sfi__ERC721.sol#305)
	Event emitted after the call(s):
	- URI(_tokenURI,tokenId) (sfi__ERC721.sol#829)
		- _setTokenURI(newItemId,tokenURI) (sfi__ERC721.sol#913)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

Address.isContract(address) (sfi__ERC721.sol#276-280) uses assembly
	- INLINE ASM (sfi__ERC721.sol#278)
Address._verifyCallResult(bool,bytes,string) (sfi__ERC721.sol#331-344) uses assembly
	- INLINE ASM (sfi__ERC721.sol#336-339)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

Address.functionCall(address,bytes) (sfi__ERC721.sol#289-291) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256) (sfi__ERC721.sol#297-299) is never used and should be removed
Address.functionDelegateCall(address,bytes) (sfi__ERC721.sol#320-322) is never used and should be removed
Address.functionDelegateCall(address,bytes,string) (sfi__ERC721.sol#324-329) is never used and should be removed
Address.functionStaticCall(address,bytes) (sfi__ERC721.sol#309-311) is never used and should be removed
Address.functionStaticCall(address,bytes,string) (sfi__ERC721.sol#313-318) is never used and should be removed
Address.sendValue(address,uint256) (sfi__ERC721.sol#282-287) is never used and should be removed
Context._msgData() (sfi__ERC721.sol#532-535) is never used and should be removed
EnumerableMap._get(EnumerableMap.Map,bytes32) (sfi__ERC721.sol#100-104) is never used and should be removed
EnumerableMap._tryGet(EnumerableMap.Map,bytes32) (sfi__ERC721.sol#94-98) is never used and should be removed
EnumerableMap.get(EnumerableMap.UintToAddressMap,uint256) (sfi__ERC721.sol#142-144) is never used and should be removed
EnumerableMap.tryGet(EnumerableMap.UintToAddressMap,uint256) (sfi__ERC721.sol#137-140) is never used and should be removed
EnumerableSet.add(EnumerableSet.AddressSet,address) (sfi__ERC721.sol#229-231) is never used and should be removed
EnumerableSet.add(EnumerableSet.Bytes32Set,bytes32) (sfi__ERC721.sol#205-207) is never used and should be removed
EnumerableSet.at(EnumerableSet.AddressSet,uint256) (sfi__ERC721.sol#245-247) is never used and should be removed
EnumerableSet.at(EnumerableSet.Bytes32Set,uint256) (sfi__ERC721.sol#221-223) is never used and should be removed
EnumerableSet.contains(EnumerableSet.AddressSet,address) (sfi__ERC721.sol#237-239) is never used and should be removed
EnumerableSet.contains(EnumerableSet.Bytes32Set,bytes32) (sfi__ERC721.sol#213-215) is never used and should be removed
EnumerableSet.contains(EnumerableSet.UintSet,uint256) (sfi__ERC721.sol#261-263) is never used and should be removed
EnumerableSet.length(EnumerableSet.AddressSet) (sfi__ERC721.sol#241-243) is never used and should be removed
EnumerableSet.length(EnumerableSet.Bytes32Set) (sfi__ERC721.sol#217-219) is never used and should be removed
EnumerableSet.remove(EnumerableSet.AddressSet,address) (sfi__ERC721.sol#233-235) is never used and should be removed
EnumerableSet.remove(EnumerableSet.Bytes32Set,bytes32) (sfi__ERC721.sol#209-211) is never used and should be removed
SafeMath.add(uint256,uint256) (sfi__ERC721.sol#386-390) is never used and should be removed
SafeMath.div(uint256,uint256) (sfi__ERC721.sol#418-421) is never used and should be removed
SafeMath.mod(uint256,uint256) (sfi__ERC721.sol#427-430) is never used and should be removed
SafeMath.mul(uint256,uint256) (sfi__ERC721.sol#406-411) is never used and should be removed
SafeMath.sub(uint256,uint256) (sfi__ERC721.sol#397-400) is never used and should be removed
SafeMath.tryAdd(uint256,uint256) (sfi__ERC721.sol#354-358) is never used and should be removed
SafeMath.tryDiv(uint256,uint256) (sfi__ERC721.sol#372-375) is never used and should be removed
SafeMath.tryMod(uint256,uint256) (sfi__ERC721.sol#377-380) is never used and should be removed
SafeMath.tryMul(uint256,uint256) (sfi__ERC721.sol#365-370) is never used and should be removed
SafeMath.trySub(uint256,uint256) (sfi__ERC721.sol#360-363) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Low level call in Address.sendValue(address,uint256) (sfi__ERC721.sol#282-287):
	- (success) = recipient.call{value: amount}() (sfi__ERC721.sol#285)
Low level call in Address.functionCallWithValue(address,bytes,uint256,string) (sfi__ERC721.sol#301-307):
	- (success,returndata) = target.call{value: value}(data) (sfi__ERC721.sol#305)
Low level call in Address.functionStaticCall(address,bytes,string) (sfi__ERC721.sol#313-318):
	- (success,returndata) = target.staticcall(data) (sfi__ERC721.sol#316)
Low level call in Address.functionDelegateCall(address,bytes,string) (sfi__ERC721.sol#324-329):
	- (success,returndata) = target.delegatecall(data) (sfi__ERC721.sol#327)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#low-level-calls

Event IERC721tokenBaseURI(string) (sfi__ERC721.sol#478) is not in CapWords
Parameter ERC721.safeTransferFrom(address,address,uint256,bytes)._data (sfi__ERC721.sol#730) is not in mixedCase
Contract collectibleds (sfi__ERC721.sol#862-926) is not in CapWords
Parameter collectibleds.setBaseURI(string)._baseURI (sfi__ERC721.sol#918) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

Redundant expression "this (sfi__ERC721.sol#533)" inContext (sfi__ERC721.sol#527-536)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#redundant-statements

supportsInterface(bytes4) should be declared external:
	- ERC165.supportsInterface(bytes4) (sfi__ERC721.sol#458-460)
balanceOf(address) should be declared external:
	- ERC721.balanceOf(address) (sfi__ERC721.sol#600-603)
name() should be declared external:
	- ERC721.name() (sfi__ERC721.sol#615-617)
symbol() should be declared external:
	- ERC721.symbol() (sfi__ERC721.sol#619-621)
tokenURI(uint256) should be declared external:
	- ERC721.tokenURI(uint256) (sfi__ERC721.sol#623-636)
royaltyFee(uint256) should be declared external:
	- ERC721.royaltyFee(uint256) (sfi__ERC721.sol#642-644)
getCreator(uint256) should be declared external:
	- ERC721.getCreator(uint256) (sfi__ERC721.sol#646-648)
tokenOfOwnerByIndex(address,uint256) should be declared external:
	- ERC721.tokenOfOwnerByIndex(address,uint256) (sfi__ERC721.sol#650-652)
totalSupply() should be declared external:
	- ERC721.totalSupply() (sfi__ERC721.sol#654-656)
tokenByIndex(uint256) should be declared external:
	- ERC721.tokenByIndex(uint256) (sfi__ERC721.sol#658-661)
approve(address,uint256) should be declared external:
	- ERC721.approve(address,uint256) (sfi__ERC721.sol#663-672)
setApprovalForAll(address,bool) should be declared external:
	- ERC721.setApprovalForAll(address,bool) (sfi__ERC721.sol#687-692)
transferFrom(address,address,uint256) should be declared external:
	- ERC721.transferFrom(address,address,uint256) (sfi__ERC721.sol#705-709)
safeTransferFrom(address,address,uint256) should be declared external:
	- ERC721.safeTransferFrom(address,address,uint256) (sfi__ERC721.sol#711-713)
transferOwnership(address) should be declared external:
	- collectibleds.transferOwnership(address) (sfi__ERC721.sol#886-891)
createCollectible(string,uint256,collectibleds.Sign) should be declared external:
	- collectibleds.createCollectible(string,uint256,collectibleds.Sign) (sfi__ERC721.sol#907-916)
setBaseURI(string) should be declared external:
	- collectibleds.setBaseURI(string) (sfi__ERC721.sol#918-920)
burn(uint256) should be declared external:
	- collectibleds.burn(uint256) (sfi__ERC721.sol#922-925)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external
. analyzed (14 contracts with 77 detectors), 78 result(s) found
