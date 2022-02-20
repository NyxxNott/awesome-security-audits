TransferProxy : 0x2de55A5e7C97A7D810e1e0e90B2c6DA6188479eE

solc-0.8.12 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Event TransferProxyoperatorChanged(address,address) (sfi__transferproxy.sol#206) is not in CapWords
Parameter TransferProxy.changeOperator(address)._operator (sfi__transferproxy.sol#235) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

changeOperator(address) should be declared external:
	- TransferProxy.changeOperator(address) (sfi__transferproxy.sol#235-240)
transferOwnership(address) should be declared external:
	- TransferProxy.transferOwnership(address) (sfi__transferproxy.sol#245-250)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external
