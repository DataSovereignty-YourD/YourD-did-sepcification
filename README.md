# YourD DID Specification
YourD-did-specification which is conforming W3C-DID-Specification
## Motivation 

In the past, there existed a sacred contract of inviolable human ownership. Today, we believe that **a second ownership revolution is taking place in the digital realm**. This revolution is centered around **digital ownership**. Indeed, all derivative data and activities that occur when individuals utilize digital services belong to the individual. Numerous tech giants and traditional companies have amassed substantial profits by exploiting our data, utilizing it for targeted advertising and financial services. Our objective is to reclaim our rights from these entities and redefine the perception surrounding digital ownership. This entails establishing data sovereignty over ourselves.

Europe and North America are advocating for robust data laws such as GDPR and ADDPA. They seek a new paradigm, a game-changer. Our aim is to build the most crucial infrastructure and services with privacy as the foundation, thereby enabling the emergence of a monumental movement known as Web3. This is the essence of YourD service.

We have identified three fundamental components for constructing Web3 services: **prove, own, and apply**. These components must remain distinct. YourD encompasses the prove and own aspects, empowering individuals to validate and assert their ownership.
## Goal
We will **ignite a revolution in digital data ownership**, which will be the cornerstone of the forthcoming Fourth Industrial Revolution and the fundamental rule of the digital world going forward 
## YourD DID Identifier Syntax
DID Method Name: YourD<br>
DID Method Specific Identifier: We provide a DID (Decentralized Identifier) specification identifier based on blockchain accounts.<br>
The method identifier in YourD follows the format: **[blockchain identifier]:[network identifier]:[blockchain account]**. The blockchain identifier represents the specific blockchain being used, such as Ethereum, Klaytn, Tezos, and others. The network identifier refers to the network associated with the blockchain, which can be mainnet, testnet, or other designated networks. The blockchain account represents the supported account type in the blockchain.

To align with the DID specification, we can express it in a more concise and standardized format as follows:

The method identifier in YourD conforms to the format specified by the DID specification. It consists of the blockchain identifier, network identifier, and blockchain account. The blockchain identifier signifies the specific blockchain being utilized, such as Ethereum, Klaytn, Tezos, and others. The network identifier pertains to the network associated with the blockchain, which can include mainnet, testnet, or other designated networks. The blockchain account represents the supported account type within the blockchain. The supported cryptographic curves for the blockchain account include:
| Key Type      | Description                                                        |
| ------------- | ------------------------------------------------------------------ |
| Ed25519 keys  | Elliptic Curve Digital Signature Algorithm (EdDSA) based on the Ed25519 curve. |
| Secp256k1 keys | Elliptic Curve Digital Signature Algorithm (ECDSA) based on the secp256k1 curve. |
| NIST P256 keys| Elliptic Curve Digital Signature Algorithm (ECDSA) based on the NIST P-256 curve. |


The supported blockchain networks currently include Ed25519 keys, Secp256k1 keys, and NIST P256 keys. These key types are widely utilized in various digital identity protocols and standards, offering robust cryptographic capabilities to establish trusted digital identities.
In a blockchain-based identity management system, these key types can be used as part of a DID to create a unique and secure identifier. A DID represents the digital identity of a specific entity, such as an individual, organization, or asset. It is associated with a blockchain account, enabling identity verification and management of digital asset ownership.

## Example

```
- did:yourd:klaytn:cypress:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58
- did:yourd:klaytn:baobab:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58
```
## YourD DID Document

The basic structure of a DID document in YourD is as follows:
```
{
   "@context":[
      "https://www.w3.org/ns/did/v1",
      "https://ns.did.ai/suites/secp256k1-2019/v1/"
   ],
   "id":"did:klaytn:baobab:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58",
   "verificationMethod":[
      {
         "id":"did:klaytn:baobab:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58#key-default",
         "type":"EcdsaSecp256k1VerificationKey2019",
         "controller":"did:klaytn:baobab:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58",
         "publicKeyMultibase":"A_Huy4IDtm0reCw0AgvZ-PbOKXaNpjcLbxCdCK3iBzky"
      }
   ],
   "authentication":[
      "did:klaytn:baobab:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58#key-default"
   ],
   "assertionMethod":[
      "did:klaytn:baobab:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58#key-default"
   ]
}
```
This JSON object is a Decentralized Identifier (DID) Document, conforming to the W3C's DID Specification. Each property has the following meanings:
- `@context`: This property specifies the standard or specification to which this DID Document conforms. In this case, it shows that the W3C's DID v1 standard and the secp256k1 cryptographic suite are used.
- `id`: This property is a unique identifier for the DID Document, used to reference this Document. Here, the ID is "did:klaytn:baobab:0xA738931B9Dd4019D282D9cf368644fEc52e9ec58".
- `verificationMethod`: This property contains an array of methods that the DID owner can use to prove their identity. The objects within this array contain the following properties:
- `id`: The unique identifier for this verification method.
- `type`: The type of the verification method. Here, it's "EcdsaSecp256k1VerificationKey2019".
- `controller`: The DID that controls the verification method.
- `publicKeyMultibase`: A public key encoded in Multibase.
- `authentication`: This property includes an array of IDs for verification methods that can be used for authentication using this DID.
- `assertionMethod`: This property includes an array of IDs for verification methods that can be used to make claims or signatures using this DID.

For detailed information on the DID Document, you can refer to the W3C's DID Specification document.
## Operation
## Privacy / Security Consideration
블록체인 네트워크에서 제공되는 Ed25519 keys, Secp256k1 keys, NIST P256 keys는 현재 많은 디지털 신원(ID) 프로토콜과 표준에서 사용되는 키 유형입니다. 이러한 키들은 안전하고 강력한 암호학적 기능을 제공하여 신뢰할 수 있는 디지털 신원을 만들 수 있습니다.

블록체인 기반의 신원 관리 시스템에서 이러한 키 유형을 사용하여 DID(Distributed Identifier)의 일부로 사용할 수 있습니다. DID는 고유한 식별자로서, 특정 개체(개인, 조직, 자산 등)의 디지털 신원을 나타냅니다. DID는 블록체인 네트워크의 account와 연결되어 있으며, 이를 통해 신원 검증과 디지털 자산 소유를 관리할 수 있습니다.
## Reference
