# SharpChain
Lite version of the Blockchain. C# Data integrity.

A light-weight framework that reads/writes to a blockchain file.

## BlockchainLite
This lite version of Blockchain reads and writes to a local blockchain. With SharpChain, it's easy to check for inconsistencies and tampering of data

### Blockchain Block Format


| **Field**        | **Size (bytes)** | **Description**                        |
|------------------|:----------------:|----------------------------------------|
| `Magic`          | 4                | Unsigned 32-bit integer identifier     |
| `Block Format`   | 1                | Format version of the block (uint8)    |
| `Timestamp`      | 4                | Signed 32-bit integer, in seconds      |
| `Data Length`    | 4                | Length of the following data (uint32)  |
| `Data`           | Variable         | Arbitrary data (length from above)     |
| `Previous Hash`  | 64               | Hash of the previous block (byte array)|
| `Block Hash`     | 64               | Hash of this block (byte array)        |
| `Owner Length`   | 4                | Length of the owner field (uint32)     |
| `Owner Text`     | Variable         | Owner name or metadata (byte array)    |
| `Terminator`     | 1                | End-of-block marker (uint8)            |

### Hash Calculation

The sha256 hash is created by concatenating the following:

`MasterKey+(Timestamp (in seconds(string)) + Previous Hash(string) + Data.Length(string) + Data(string) + Owner.Length(string) + Owner(string))`

Providing a format other than that will create inconsistencies with the data.

### Data inconsistencies

SharpChain checks for two types of data inconsistencies.

* Tampering with data
* Altering hashes.

Either will cause all future blocks to be inconsistent.

## Genesis Block

The initial Block Hash should always equal 64 '0's .

## Inconsistency check

After running your applciation (which will build a database), do some hex-editing then run the application again :).

## Blockchain Path

You can set the Blockchain file path by setting SharpChain.basedir = ("c:\\path-to-file\\", "/var/usr/blockchains/")

### Credits
* [https://guns.lol/ctvs](ctvs)
