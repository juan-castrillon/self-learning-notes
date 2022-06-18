---
title: Numeric Types
parent: Basic Types
grand_parent: Go
---

# Supported Numeric Types

| Data Type  	| Description                       	|
|------------	|-----------------------------------	|
| `int8`       	| 8-bit signed integer              	|
| `int16`      	| 16-bit signed integer             	|
| `int32`      	| 32-bit signed integer             	|
| `int64`      	| 64-bit signed integer             	|
| `int`        	| 32- or 64-bit signed integer      	|
| `uint8`      	| 8-bit unsigned integer            	|
| `uint16`     	| 16-bit unsigned integer           	|
| `uint32`     	| 32-bit unsigned integer           	|
| `uint64`     	| 64-bit unsigned integer           	|
| `uint`       	| 32- or 64-bit unsigned integer    	|
| `float32`    	| 32-bit floating-point number      	|
| `float64`    	| 64-bit floating-point number      	|
| `complex64`  	| Complex number with float32 parts 	|
| `Complex128` 	| Complex number with float64 parts 	|

# Notes

- `int` and `uint` are the most efficient size of each platform an can be 32 or 64 bits (`go` chooses)
- Implicit data conversion does NOT exist in go, this is important when considering operations between types (`float` and `int` for example)