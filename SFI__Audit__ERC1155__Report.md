ERC1155 : 0x8704F5D561C5Da161A77297fd0A9a156ed427793

ERC1155._doSafeTransferAcceptanceCheck(address,address,address,uint256,uint256,bytes).response (sfi__ERC1155__001.sol#892) is a local variable never initialized
ERC1155._doSafeBatchTransferAcceptanceCheck(address,address,address,uint256[],uint256[],bytes).reason (sfi__ERC1155__001.sol#919) is a local variable never initialized
ERC1155._doSafeBatchTransferAcceptanceCheck(address,address,address,uint256[],uint256[],bytes).response (sfi__ERC1155__001.sol#915) is a local variable never initialized
ERC1155._doSafeTransferAcceptanceCheck(address,address,address,uint256,uint256,bytes).reason (sfi__ERC1155__001.sol#896) is a local variable never initialized
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#uninitialized-local-variables

ERC1155._mint(uint256,uint256,string,uint256) (sfi__ERC1155__001.sol#778-791) ignores return value by _tokenOwners.set(tokenId,msg.sender) (sfi__ERC1155__001.sol#784)
ERC1155._doSafeTransferAcceptanceCheck(address,address,address,uint256,uint256,bytes) (sfi__ERC1155__001.sol#881-902) ignores return value by IERC1155Receiver(to).onERC1155Received(operator,from,tokenId,amount,data) (sfi__ERC1155__001.sol#892-900)
ERC1155._doSafeBatchTransferAcceptanceCheck(address,address,address,uint256[],uint256[],bytes) (sfi__ERC1155__001.sol#904-925) ignores return value by IERC1155Receiver(to).onERC1155BatchReceived(operator,from,tokenIds,amounts,data) (sfi__ERC1155__001.sol#915-923)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#unused-return

collectibledm.constructor(string,string).name (sfi__ERC1155__001.sol#949) shadows:
	- ERC1155.name() (sfi__ERC1155__001.sol#528-530) (function)
	- IERC1155.name() (sfi__ERC1155__001.sol#297) (function)
collectibledm.constructor(string,string).symbol (sfi__ERC1155__001.sol#949) shadows:
	- ERC1155.symbol() (sfi__ERC1155__001.sol#532-534) (function)
	- IERC1155.symbol() (sfi__ERC1155__001.sol#298) (function)
collectibledm.verifySign(string,address,collectibledm.Sign).tokenURI (sfi__ERC1155__001.sol#976) shadows:
	- ERC1155.tokenURI(uint256) (sfi__ERC1155__001.sol#583-595) (function)
	- IERC1155.tokenURI(uint256) (sfi__ERC1155__001.sol#302) (function)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#local-variable-shadowing

Variable 'ERC1155._doSafeTransferAcceptanceCheck(address,address,address,uint256,uint256,bytes).response (sfi__ERC1155__001.sol#892)' in ERC1155._doSafeTransferAcceptanceCheck(address,address,address,uint256,uint256,bytes) (sfi__ERC1155__001.sol#881-902) potentially used before declaration: response != IERC1155Receiver(to).onERC1155Received.selector (sfi__ERC1155__001.sol#893)
Variable 'ERC1155._doSafeTransferAcceptanceCheck(address,address,address,uint256,uint256,bytes).reason (sfi__ERC1155__001.sol#896)' in ERC1155._doSafeTransferAcceptanceCheck(address,address,address,uint256,uint256,bytes) (sfi__ERC1155__001.sol#881-902) potentially used before declaration: revert(string)(reason) (sfi__ERC1155__001.sol#897)
Variable 'ERC1155._doSafeBatchTransferAcceptanceCheck(address,address,address,uint256[],uint256[],bytes).response (sfi__ERC1155__001.sol#915)' in ERC1155._doSafeBatchTransferAcceptanceCheck(address,address,address,uint256[],uint256[],bytes) (sfi__ERC1155__001.sol#904-925) potentially used before declaration: response != IERC1155Receiver(to).onERC1155BatchReceived.selector (sfi__ERC1155__001.sol#916)
Variable 'ERC1155._doSafeBatchTransferAcceptanceCheck(address,address,address,uint256[],uint256[],bytes).reason (sfi__ERC1155__001.sol#919)' in ERC1155._doSafeBatchTransferAcceptanceCheck(address,address,address,uint256[],uint256[],bytes) (sfi__ERC1155__001.sol#904-925) potentially used before declaration: revert(string)(reason) (sfi__ERC1155__001.sol#920)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#pre-declaration-usage-of-local-variables

Address.isContract(address) (sfi__ERC1155__001.sol#442-446) uses assembly
	- INLINE ASM (sfi__ERC1155__001.sol#444)
Address._functionCallWithValue(address,bytes,uint256,string) (sfi__ERC1155__001.sol#472-489) uses assembly
	- INLINE ASM (sfi__ERC1155__001.sol#481-484)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

Address._functionCallWithValue(address,bytes,uint256,string) (sfi__ERC1155__001.sol#472-489) is never used and should be removed
Address.functionCall(address,bytes) (sfi__ERC1155__001.sol#455-457) is never used and should be removed
Address.functionCall(address,bytes,string) (sfi__ERC1155__001.sol#459-461) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256) (sfi__ERC1155__001.sol#463-465) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256,string) (sfi__ERC1155__001.sol#467-470) is never used and should be removed
Address.sendValue(address,uint256) (sfi__ERC1155__001.sol#448-453) is never used and should be removed
Context._msgData() (sfi__ERC1155__001.sol#340-343) is never used and should be removed
ERC1155._mintBatch(address,uint256[],uint256[],bytes) (sfi__ERC1155__001.sol#801-816) is never used and should be removed
EnumerableMap._at(EnumerableMap.Map,uint256) (sfi__ERC1155__001.sol#87-92) is never used and should be removed
EnumerableMap._get(EnumerableMap.Map,bytes32) (sfi__ERC1155__001.sol#100-104) is never used and should be removed
EnumerableMap._get(EnumerableMap.Map,bytes32,string) (sfi__ERC1155__001.sol#106-110) is never used and should be removed
EnumerableMap._length(EnumerableMap.Map) (sfi__ERC1155__001.sol#83-85) is never used and should be removed
EnumerableMap._remove(EnumerableMap.Map,bytes32) (sfi__ERC1155__001.sol#58-77) is never used and should be removed
EnumerableMap._tryGet(EnumerableMap.Map,bytes32) (sfi__ERC1155__001.sol#94-98) is never used and should be removed
EnumerableMap.at(EnumerableMap.UintToAddressMap,uint256) (sfi__ERC1155__001.sol#132-135) is never used and should be removed
EnumerableMap.get(EnumerableMap.UintToAddressMap,uint256) (sfi__ERC1155__001.sol#142-144) is never used and should be removed
EnumerableMap.get(EnumerableMap.UintToAddressMap,uint256,string) (sfi__ERC1155__001.sol#146-148) is never used and should be removed
EnumerableMap.length(EnumerableMap.UintToAddressMap) (sfi__ERC1155__001.sol#128-130) is never used and should be removed
EnumerableMap.remove(EnumerableMap.UintToAddressMap,uint256) (sfi__ERC1155__001.sol#120-122) is never used and should be removed
EnumerableMap.tryGet(EnumerableMap.UintToAddressMap,uint256) (sfi__ERC1155__001.sol#137-140) is never used and should be removed
EnumerableSet._add(EnumerableSet.Set,bytes32) (sfi__ERC1155__001.sol#157-165) is never used and should be removed
EnumerableSet._at(EnumerableSet.Set,uint256) (sfi__ERC1155__001.sol#196-199) is never used and should be removed
EnumerableSet._contains(EnumerableSet.Set,bytes32) (sfi__ERC1155__001.sol#188-190) is never used and should be removed
EnumerableSet._length(EnumerableSet.Set) (sfi__ERC1155__001.sol#192-194) is never used and should be removed
EnumerableSet._remove(EnumerableSet.Set,bytes32) (sfi__ERC1155__001.sol#167-186) is never used and should be removed
EnumerableSet.add(EnumerableSet.AddressSet,address) (sfi__ERC1155__001.sol#229-231) is never used and should be removed
EnumerableSet.add(EnumerableSet.Bytes32Set,bytes32) (sfi__ERC1155__001.sol#205-207) is never used and should be removed
EnumerableSet.add(EnumerableSet.UintSet,uint256) (sfi__ERC1155__001.sol#253-255) is never used and should be removed
EnumerableSet.at(EnumerableSet.AddressSet,uint256) (sfi__ERC1155__001.sol#245-247) is never used and should be removed
EnumerableSet.at(EnumerableSet.Bytes32Set,uint256) (sfi__ERC1155__001.sol#221-223) is never used and should be removed
EnumerableSet.at(EnumerableSet.UintSet,uint256) (sfi__ERC1155__001.sol#269-271) is never used and should be removed
EnumerableSet.contains(EnumerableSet.AddressSet,address) (sfi__ERC1155__001.sol#237-239) is never used and should be removed
EnumerableSet.contains(EnumerableSet.Bytes32Set,bytes32) (sfi__ERC1155__001.sol#213-215) is never used and should be removed
EnumerableSet.contains(EnumerableSet.UintSet,uint256) (sfi__ERC1155__001.sol#261-263) is never used and should be removed
EnumerableSet.length(EnumerableSet.AddressSet) (sfi__ERC1155__001.sol#241-243) is never used and should be removed
EnumerableSet.length(EnumerableSet.Bytes32Set) (sfi__ERC1155__001.sol#217-219) is never used and should be removed
EnumerableSet.length(EnumerableSet.UintSet) (sfi__ERC1155__001.sol#265-267) is never used and should be removed
EnumerableSet.remove(EnumerableSet.AddressSet,address) (sfi__ERC1155__001.sol#233-235) is never used and should be removed
EnumerableSet.remove(EnumerableSet.Bytes32Set,bytes32) (sfi__ERC1155__001.sol#209-211) is never used and should be removed
EnumerableSet.remove(EnumerableSet.UintSet,uint256) (sfi__ERC1155__001.sol#257-259) is never used and should be removed
SafeMath.div(uint256,uint256) (sfi__ERC1155__001.sol#416-418) is never used and should be removed
SafeMath.div(uint256,uint256,string) (sfi__ERC1155__001.sol#420-424) is never used and should be removed
SafeMath.mod(uint256,uint256) (sfi__ERC1155__001.sol#430-432) is never used and should be removed
SafeMath.mod(uint256,uint256,string) (sfi__ERC1155__001.sol#434-437) is never used and should be removed
SafeMath.mul(uint256,uint256) (sfi__ERC1155__001.sol#401-410) is never used and should be removed
SafeMath.sub(uint256,uint256) (sfi__ERC1155__001.sol#386-388) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Low level call in Address.sendValue(address,uint256) (sfi__ERC1155__001.sol#448-453):
	- (success) = recipient.call{value: amount}() (sfi__ERC1155__001.sol#451)
Low level call in Address._functionCallWithValue(address,bytes,uint256,string) (sfi__ERC1155__001.sol#472-489):
	- (success,returndata) = target.call{value: weiValue}(data) (sfi__ERC1155__001.sol#475)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#low-level-calls

Event IERC1155tokenBaseURI(string) (sfi__ERC1155__001.sol#294) is not in CapWords
Contract collectibledm (sfi__ERC1155__001.sol#935-1000) is not in CapWords
Parameter collectibledm.setBaseURI(string)._baseURI (sfi__ERC1155__001.sol#989) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

Redundant expression "this (sfi__ERC1155__001.sol#341)" inContext (sfi__ERC1155__001.sol#335-344)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#redundant-statements

supportsInterface(bytes4) should be declared external:
	- ERC165.supportsInterface(bytes4) (sfi__ERC1155__001.sol#354-356)
name() should be declared external:
	- ERC1155.name() (sfi__ERC1155__001.sol#528-530)
symbol() should be declared external:
	- ERC1155.symbol() (sfi__ERC1155__001.sol#532-534)
royaltyFee(uint256) should be declared external:
	- ERC1155.royaltyFee(uint256) (sfi__ERC1155__001.sol#553-555)
getCreator(uint256) should be declared external:
	- ERC1155.getCreator(uint256) (sfi__ERC1155__001.sol#563-565)
tokenURI(uint256) should be declared external:
	- ERC1155.tokenURI(uint256) (sfi__ERC1155__001.sol#583-595)
balanceOf(address,uint256) should be declared external:
	- ERC1155.balanceOf(address,uint256) (sfi__ERC1155__001.sol#608-612)
balanceOfBatch(address[],uint256[]) should be declared external:
	- ERC1155.balanceOfBatch(address[],uint256[]) (sfi__ERC1155__001.sol#622-641)
setApprovalForAll(address,bool) should be declared external:
	- ERC1155.setApprovalForAll(address,bool) (sfi__ERC1155__001.sol#650-655)
safeTransferFrom(address,address,uint256,uint256,bytes) should be declared external:
	- ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes) (sfi__ERC1155__001.sol#683-710)
safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) should be declared external:
	- ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (sfi__ERC1155__001.sol#729-765)
transferOwnership(address) should be declared external:
	- collectibledm.transferOwnership(address) (sfi__ERC1155__001.sol#961-966)
mint(string,uint256,uint256,collectibledm.Sign) should be declared external:
	- collectibledm.mint(string,uint256,uint256,collectibledm.Sign) (sfi__ERC1155__001.sol#981-987)
setBaseURI(string) should be declared external:
	- collectibledm.setBaseURI(string) (sfi__ERC1155__001.sol#989-991)
burn(uint256,uint256) should be declared external:
	- collectibledm.burn(uint256,uint256) (sfi__ERC1155__001.sol#993-995)
burnBatch(uint256[],uint256[]) should be declared external:
	- collectibledm.burnBatch(uint256[],uint256[]) (sfi__ERC1155__001.sol#997-999)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external
. analyzed (13 contracts with 77 detectors), 85 result(s) found

