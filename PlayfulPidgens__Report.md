## Contract Address
- https://rinkeby.etherscan.io/address/0x5a80752eaEb8Adc91Ac755B1a4DA7f66a9A73950#code

## Contract Audit Report

Context._msgData() (Context.sol#21-23) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.8.0 (Context.sol#4) allows old versions
Pragma version^0.8.0 (Ownable.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

renounceOwnership() should be declared external:
	- Ownable.renounceOwnership() (Ownable.sol#54-56)
transferOwnership(address) should be declared external:
	- Ownable.transferOwnership(address) (Ownable.sol#62-65)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external

Address.isContract(address) (Address.sol#27-37) uses assembly
	- INLINE ASM (Address.sol#33-35)
Address.verifyCallResult(bool,bytes,string) (Address.sol#196-216) uses assembly
	- INLINE ASM (Address.sol#208-211)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

Address.functionCall(address,bytes) (Address.sol#80-82) is never used and should be removed
Address.functionCall(address,bytes,string) (Address.sol#90-96) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256) (Address.sol#109-115) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256,string) (Address.sol#123-134) is never used and should be removed
Address.functionDelegateCall(address,bytes) (Address.sol#169-171) is never used and should be removed
Address.functionDelegateCall(address,bytes,string) (Address.sol#179-188) is never used and should be removed
Address.functionStaticCall(address,bytes) (Address.sol#142-144) is never used and should be removed
Address.functionStaticCall(address,bytes,string) (Address.sol#152-161) is never used and should be removed
Address.isContract(address) (Address.sol#27-37) is never used and should be removed
Address.sendValue(address,uint256) (Address.sol#55-60) is never used and should be removed
Address.verifyCallResult(bool,bytes,string) (Address.sol#196-216) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.8.0 (Address.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Low level call in Address.sendValue(address,uint256) (Address.sol#55-60):
	- (success) = recipient.call{value: amount}() (Address.sol#58)
Low level call in Address.functionCallWithValue(address,bytes,uint256,string) (Address.sol#123-134):
	- (success,returndata) = target.call{value: value}(data) (Address.sol#132)
Low level call in Address.functionStaticCall(address,bytes,string) (Address.sol#152-161):
	- (success,returndata) = target.staticcall(data) (Address.sol#159)
Low level call in Address.functionDelegateCall(address,bytes,string) (Address.sol#179-188):
	- (success,returndata) = target.delegatecall(data) (Address.sol#186)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#low-level-calls

Pragma version^0.8.0 (IERC165.sol#4) allows old versions
Pragma version^0.8.0 (IERC721.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Metadata.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

ERC721A._transfer(address,address,uint256) (ERC721A.sol#398-443) uses a dangerous strict equality:
	- _ownerships[nextTokenId].addr == address(0) (ERC721A.sol#432)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dangerous-strict-equalities

Reentrancy in Playfuldegens.claimPreSaleToken(uint256) (NFT.sol#44-63):
	External calls:
	- _safeMint(msg.sender,numberOfTokens) (NFT.sol#59)
		- IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) (ERC721A.sol#502-514)
	State variables written after the call(s):
	- _userSaleMints[msg.sender] += numberOfTokens (NFT.sol#60)
	- presaleWalletList[msg.sender] = false (NFT.sol#62)
Reentrancy in Playfuldegens.claimTheToken(uint256) (NFT.sol#66-77):
	External calls:
	- _safeMint(msg.sender,numberOfTokens) (NFT.sol#75)
		- IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) (ERC721A.sol#502-514)
	State variables written after the call(s):
	- _userSaleMints[msg.sender] += numberOfTokens (NFT.sol#76)
Reentrancy in Playfuldegens.releaseReserved(address) (NFT.sol#31-35):
	External calls:
	- _safeMint(userAddress,1) (NFT.sol#33)
		- IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) (ERC721A.sol#502-514)
	State variables written after the call(s):
	- RESERVED_MINTS_AVAILABLE -- (NFT.sol#34)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1

ERC721A.ownershipOf(uint256).lowestTokenToCheck (ERC721A.sol#175) is a local variable never initialized
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#uninitialized-local-variables

ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) ignores return value by IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) (ERC721A.sol#502-514)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#unused-return

Variable 'ERC721A._checkOnERC721Received(address,address,uint256,bytes).retval (ERC721A.sol#504)' in ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) potentially used before declaration: retval == IERC721Receiver(to).onERC721Received.selector (ERC721A.sol#505)
Variable 'ERC721A._checkOnERC721Received(address,address,uint256,bytes).reason (ERC721A.sol#506)' in ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) potentially used before declaration: reason.length == 0 (ERC721A.sol#507)
Variable 'ERC721A._checkOnERC721Received(address,address,uint256,bytes).reason (ERC721A.sol#506)' in ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) potentially used before declaration: revert(uint256,uint256)(32 + reason,mload(uint256)(reason)) (ERC721A.sol#511)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#pre-declaration-usage-of-local-variables

ERC721A._transfer(address,address,uint256) (ERC721A.sol#398-443) uses timestamp for comparisons
	Dangerous comparisons:
	- _ownerships[nextTokenId].addr == address(0) (ERC721A.sol#432)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp

Address.isContract(address) (Address.sol#27-37) uses assembly
	- INLINE ASM (Address.sol#33-35)
Address.verifyCallResult(bool,bytes,string) (Address.sol#196-216) uses assembly
	- INLINE ASM (Address.sol#208-211)
ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) uses assembly
	- INLINE ASM (ERC721A.sol#510-512)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

Playfuldegens.claimPreSaleToken(uint256) (NFT.sol#44-63) compares to a boolean constant:
	-require(bool,string)(presaleWalletList[msg.sender] == true,You are not on the presale wallet list or have already minted) (NFT.sol#54-57)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#boolean-equality

Address.functionCall(address,bytes) (Address.sol#80-82) is never used and should be removed
Address.functionCall(address,bytes,string) (Address.sol#90-96) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256) (Address.sol#109-115) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256,string) (Address.sol#123-134) is never used and should be removed
Address.functionDelegateCall(address,bytes) (Address.sol#169-171) is never used and should be removed
Address.functionDelegateCall(address,bytes,string) (Address.sol#179-188) is never used and should be removed
Address.functionStaticCall(address,bytes) (Address.sol#142-144) is never used and should be removed
Address.functionStaticCall(address,bytes,string) (Address.sol#152-161) is never used and should be removed
Address.sendValue(address,uint256) (Address.sol#55-60) is never used and should be removed
Address.verifyCallResult(bool,bytes,string) (Address.sol#196-216) is never used and should be removed
Context._msgData() (Context.sol#21-23) is never used and should be removed
Counters.current(Counters.Counter) (Counters.sol#22-24) is never used and should be removed
Counters.decrement(Counters.Counter) (Counters.sol#32-38) is never used and should be removed
Counters.increment(Counters.Counter) (Counters.sol#26-30) is never used and should be removed
Counters.reset(Counters.Counter) (Counters.sol#40-42) is never used and should be removed
ERC721A._baseURI() (ERC721A.sol#238-240) is never used and should be removed
ERC721A._numberMinted(address) (ERC721A.sol#160-166) is never used and should be removed
ERC721A._setOwnersExplicit(uint256) (ERC721A.sol#464-483) is never used and should be removed
Strings.toHexString(uint256) (Strings.sol#40-51) is never used and should be removed
Strings.toHexString(uint256,uint256) (Strings.sol#56-66) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.8.0 (Address.sol#4) allows old versions
Pragma version^0.8.0 (Context.sol#4) allows old versions
Pragma version^0.8.0 (Counters.sol#4) allows old versions
Pragma version^0.8.0 (ERC165.sol#4) allows old versions
Pragma version^0.8.0 (ERC721A.sol#3) allows old versions
Pragma version^0.8.0 (IERC165.sol#4) allows old versions
Pragma version^0.8.0 (IERC721.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Enumerable.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Metadata.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Receiver.sol#4) allows old versions
Pragma version^0.8.0 (NFT.sol#2) allows old versions
Pragma version^0.8.0 (Ownable.sol#4) allows old versions
Pragma version^0.8.0 (Strings.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Low level call in Address.sendValue(address,uint256) (Address.sol#55-60):
	- (success) = recipient.call{value: amount}() (Address.sol#58)
Low level call in Address.functionCallWithValue(address,bytes,uint256,string) (Address.sol#123-134):
	- (success,returndata) = target.call{value: value}(data) (Address.sol#132)
Low level call in Address.functionStaticCall(address,bytes,string) (Address.sol#152-161):
	- (success,returndata) = target.staticcall(data) (Address.sol#159)
Low level call in Address.functionDelegateCall(address,bytes,string) (Address.sol#179-188):
	- (success,returndata) = target.delegatecall(data) (Address.sol#186)
Low level call in Playfuldegens.withdrawMoney() (NFT.sol#96-99):
	- (success) = msg.sender.call{value: address(this).balance}() (NFT.sol#97)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#low-level-calls

Parameter ERC721A.safeTransferFrom(address,address,uint256,bytes)._data (ERC721A.sol#318) is not in mixedCase
Variable Playfuldegens.RESERVED_MINTS_AVAILABLE (NFT.sol#12) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

Playfuldegens._tokenIds (NFT.sol#15) is never used in Playfuldegens (NFT.sol#8-114)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#unused-state-variable

tokenByIndex(uint256) should be declared external:
	- ERC721A.tokenByIndex(uint256) (ERC721A.sol#100-103)
tokenOfOwnerByIndex(address,uint256) should be declared external:
	- ERC721A.tokenOfOwnerByIndex(address,uint256) (ERC721A.sol#110-133)
name() should be declared external:
	- ERC721A.name() (ERC721A.sol#200-202)
symbol() should be declared external:
	- ERC721A.symbol() (ERC721A.sol#207-209)
tokenURI(uint256) should be declared external:
	- ERC721A.tokenURI(uint256) (ERC721A.sol#214-231)
approve(address,uint256) should be declared external:
	- ERC721A.approve(address,uint256) (ERC721A.sol#245-255)
setApprovalForAll(address,bool) should be declared external:
	- ERC721A.setApprovalForAll(address,bool) (ERC721A.sol#269-274)
transferFrom(address,address,uint256) should be declared external:
	- ERC721A.transferFrom(address,address,uint256) (ERC721A.sol#292-298)
safeTransferFrom(address,address,uint256) should be declared external:
	- ERC721A.safeTransferFrom(address,address,uint256) (ERC721A.sol#303-309)
claimPreSaleToken(uint256) should be declared external:
	- Playfuldegens.claimPreSaleToken(uint256) (NFT.sol#44-63)
claimTheToken(uint256) should be declared external:
	- Playfuldegens.claimTheToken(uint256) (NFT.sol#66-77)
renounceOwnership() should be declared external:
	- Ownable.renounceOwnership() (Ownable.sol#54-56)
transferOwnership(address) should be declared external:
	- Ownable.transferOwnership(address) (Ownable.sol#62-65)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external

Counters.current(Counters.Counter) (Counters.sol#22-24) is never used and should be removed
Counters.decrement(Counters.Counter) (Counters.sol#32-38) is never used and should be removed
Counters.increment(Counters.Counter) (Counters.sol#26-30) is never used and should be removed
Counters.reset(Counters.Counter) (Counters.sol#40-42) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.8.0 (Counters.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Strings.toHexString(uint256) (Strings.sol#40-51) is never used and should be removed
Strings.toHexString(uint256,uint256) (Strings.sol#56-66) is never used and should be removed
Strings.toString(uint256) (Strings.sol#15-35) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.8.0 (Strings.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Pragma version^0.8.0 (IERC165.sol#4) allows old versions
Pragma version^0.8.0 (IERC721.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Enumerable.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Pragma version^0.8.0 (IERC165.sol#4) allows old versions
Pragma version^0.8.0 (IERC721.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Pragma version^0.8.0 (IERC165.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Context._msgData() (Context.sol#21-23) is never used and should be removed
Context._msgSender() (Context.sol#17-19) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.8.0 (Context.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Pragma version^0.8.0 (IERC721Receiver.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

ERC721A._transfer(address,address,uint256) (ERC721A.sol#398-443) uses a dangerous strict equality:
	- _ownerships[nextTokenId].addr == address(0) (ERC721A.sol#432)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dangerous-strict-equalities

ERC721A.ownershipOf(uint256).lowestTokenToCheck (ERC721A.sol#175) is a local variable never initialized
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#uninitialized-local-variables

ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) ignores return value by IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) (ERC721A.sol#502-514)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#unused-return

Variable 'ERC721A._checkOnERC721Received(address,address,uint256,bytes).retval (ERC721A.sol#504)' in ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) potentially used before declaration: retval == IERC721Receiver(to).onERC721Received.selector (ERC721A.sol#505)
Variable 'ERC721A._checkOnERC721Received(address,address,uint256,bytes).reason (ERC721A.sol#506)' in ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) potentially used before declaration: reason.length == 0 (ERC721A.sol#507)
Variable 'ERC721A._checkOnERC721Received(address,address,uint256,bytes).reason (ERC721A.sol#506)' in ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) potentially used before declaration: revert(uint256,uint256)(32 + reason,mload(uint256)(reason)) (ERC721A.sol#511)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#pre-declaration-usage-of-local-variables

ERC721A._transfer(address,address,uint256) (ERC721A.sol#398-443) uses timestamp for comparisons
	Dangerous comparisons:
	- _ownerships[nextTokenId].addr == address(0) (ERC721A.sol#432)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp

Address.isContract(address) (Address.sol#27-37) uses assembly
	- INLINE ASM (Address.sol#33-35)
Address.verifyCallResult(bool,bytes,string) (Address.sol#196-216) uses assembly
	- INLINE ASM (Address.sol#208-211)
ERC721A._checkOnERC721Received(address,address,uint256,bytes) (ERC721A.sol#495-518) uses assembly
	- INLINE ASM (ERC721A.sol#510-512)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

Address.functionCall(address,bytes) (Address.sol#80-82) is never used and should be removed
Address.functionCall(address,bytes,string) (Address.sol#90-96) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256) (Address.sol#109-115) is never used and should be removed
Address.functionCallWithValue(address,bytes,uint256,string) (Address.sol#123-134) is never used and should be removed
Address.functionDelegateCall(address,bytes) (Address.sol#169-171) is never used and should be removed
Address.functionDelegateCall(address,bytes,string) (Address.sol#179-188) is never used and should be removed
Address.functionStaticCall(address,bytes) (Address.sol#142-144) is never used and should be removed
Address.functionStaticCall(address,bytes,string) (Address.sol#152-161) is never used and should be removed
Address.sendValue(address,uint256) (Address.sol#55-60) is never used and should be removed
Address.verifyCallResult(bool,bytes,string) (Address.sol#196-216) is never used and should be removed
Context._msgData() (Context.sol#21-23) is never used and should be removed
ERC721A._numberMinted(address) (ERC721A.sol#160-166) is never used and should be removed
ERC721A._safeMint(address,uint256) (ERC721A.sol#338-340) is never used and should be removed
ERC721A._safeMint(address,uint256,bytes) (ERC721A.sol#353-386) is never used and should be removed
ERC721A._setOwnersExplicit(uint256) (ERC721A.sol#464-483) is never used and should be removed
Strings.toHexString(uint256) (Strings.sol#40-51) is never used and should be removed
Strings.toHexString(uint256,uint256) (Strings.sol#56-66) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.8.0 (Address.sol#4) allows old versions
Pragma version^0.8.0 (Context.sol#4) allows old versions
Pragma version^0.8.0 (ERC165.sol#4) allows old versions
Pragma version^0.8.0 (ERC721A.sol#3) allows old versions
Pragma version^0.8.0 (IERC165.sol#4) allows old versions
Pragma version^0.8.0 (IERC721.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Enumerable.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Metadata.sol#4) allows old versions
Pragma version^0.8.0 (IERC721Receiver.sol#4) allows old versions
Pragma version^0.8.0 (Strings.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Low level call in Address.sendValue(address,uint256) (Address.sol#55-60):
	- (success) = recipient.call{value: amount}() (Address.sol#58)
Low level call in Address.functionCallWithValue(address,bytes,uint256,string) (Address.sol#123-134):
	- (success,returndata) = target.call{value: value}(data) (Address.sol#132)
Low level call in Address.functionStaticCall(address,bytes,string) (Address.sol#152-161):
	- (success,returndata) = target.staticcall(data) (Address.sol#159)
Low level call in Address.functionDelegateCall(address,bytes,string) (Address.sol#179-188):
	- (success,returndata) = target.delegatecall(data) (Address.sol#186)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#low-level-calls

Parameter ERC721A.safeTransferFrom(address,address,uint256,bytes)._data (ERC721A.sol#318) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

tokenByIndex(uint256) should be declared external:
	- ERC721A.tokenByIndex(uint256) (ERC721A.sol#100-103)
tokenOfOwnerByIndex(address,uint256) should be declared external:
	- ERC721A.tokenOfOwnerByIndex(address,uint256) (ERC721A.sol#110-133)
name() should be declared external:
	- ERC721A.name() (ERC721A.sol#200-202)
symbol() should be declared external:
	- ERC721A.symbol() (ERC721A.sol#207-209)
tokenURI(uint256) should be declared external:
	- ERC721A.tokenURI(uint256) (ERC721A.sol#214-231)
approve(address,uint256) should be declared external:
	- ERC721A.approve(address,uint256) (ERC721A.sol#245-255)
setApprovalForAll(address,bool) should be declared external:
	- ERC721A.setApprovalForAll(address,bool) (ERC721A.sol#269-274)
transferFrom(address,address,uint256) should be declared external:
	- ERC721A.transferFrom(address,address,uint256) (ERC721A.sol#292-298)
safeTransferFrom(address,address,uint256) should be declared external:
	- ERC721A.safeTransferFrom(address,address,uint256) (ERC721A.sol#303-309)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external

Pragma version^0.8.0 (ERC165.sol#4) allows old versions
Pragma version^0.8.0 (IERC165.sol#4) allows old versions
solc-0.8.11 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

supportsInterface(bytes4) should be declared external:
	- ERC165.supportsInterface(bytes4) (ERC165.sol#26-28)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external
. analyzed (41 contracts with 77 detectors), 180 result(s) found
