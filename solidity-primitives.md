layout: page
title: "Solidity Primitives"
permalink: /solidity-primitives

# Solidity Data Types

* Statically typed language
* Null or undefined does not exist
* Variables have a default value

Let's review the common primitive data types available in Solidity.

* uint8: 0 to 2^8 - 1 i.e. 0 to 255 in decimal base 10
* uint256: 0 up to 2^256 - 1 i.e. 0 to 57896044618658097711785492504343953926634992332820282019728792003956564819967 in decimal base 10

uint is an alias for uint256.



Primitives.sol

<script src="https://gist.github.com/anataliocs/38015973c62dfcbe08c50946115a406a.js"></script>


Solidity State after deployment
```
 boo: true bool
 u8: 1 uint8
 u256: 456 uint256
 u: 123 uint256
 i8: -1 int8
 i256: 456 int256
 i: -123 int256
 minInt: -57896044618658097711785492504343953926634992332820282019728792003956564819968 int256
 maxInt: 57896044618658097711785492504343953926634992332820282019728792003956564819967 int256
 addr: 0xCA35B7D915458EF540ADE6068DFE2F44E8FA733C address
 a: 0xB5 bytes1
 b: 0x56 bytes1
 defaultBoo: false bool
 defaultUint: 0 uint256
 defaultInt: 0 int256
 defaultAddr: 0x0000000000000000000000000000000000000000 address
```

State in JSON Format
```
{
	"boo": {
		"value": true,
		"type": "bool",
		"constant": false,
		"immutable": false
	},
	"u8": {
		"value": "1",
		"type": "uint8",
		"constant": false,
		"immutable": false
	},
	"u256": {
		"value": "456",
		"type": "uint256",
		"constant": false,
		"immutable": false
	},
	"u": {
		"value": "123",
		"type": "uint256",
		"constant": false,
		"immutable": false
	},
	"i8": {
		"value": "-1",
		"type": "int8",
		"constant": false,
		"immutable": false
	},
	"i256": {
		"value": "456",
		"type": "int256",
		"constant": false,
		"immutable": false
	},
	"i": {
		"value": "-123",
		"type": "int256",
		"constant": false,
		"immutable": false
	},
	"minInt": {
		"value": "-57896044618658097711785492504343953926634992332820282019728792003956564819968",
		"type": "int256",
		"constant": false,
		"immutable": false
	},
	"maxInt": {
		"value": "57896044618658097711785492504343953926634992332820282019728792003956564819967",
		"type": "int256",
		"constant": false,
		"immutable": false
	},
	"addr": {
		"value": "0xCA35B7D915458EF540ADE6068DFE2F44E8FA733C",
		"type": "address",
		"constant": false,
		"immutable": false
	},
	"a": {
		"value": "0xB5",
		"type": "bytes1",
		"constant": false,
		"immutable": false
	},
	"b": {
		"value": "0x56",
		"type": "bytes1",
		"constant": false,
		"immutable": false
	},
	"defaultBoo": {
		"value": false,
		"type": "bool",
		"constant": false,
		"immutable": false
	},
	"defaultUint": {
		"value": "0",
		"type": "uint256",
		"constant": false,
		"immutable": false
	},
	"defaultInt": {
		"value": "0",
		"type": "int256",
		"constant": false,
		"immutable": false
	},
	"defaultAddr": {
		"value": "0x0000000000000000000000000000000000000000",
		"type": "address",
		"constant": false,
		"immutable": false
	}
}
```
