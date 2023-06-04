# YourD DID Specification
YourD-did-specification which is conforming W3C-DID-Specification
## Motivation 

In the past, there existed a sacred contract of inviolable human ownership. Today, we believe that **a second ownership revolution is taking place in the digital realm**. This revolution is centered around **digital ownership**. Indeed, all derivative data and activities that occur when individuals utilize digital services belong to the individual. Numerous tech giants and traditional companies have amassed substantial profits by exploiting our data, utilizing it for targeted advertising and financial services. Our objective is to reclaim our rights from these entities and redefine the perception surrounding digital ownership. This entails establishing data sovereignty over ourselves.

Europe and North America are advocating for robust data laws such as GDPR and ADDPA. They seek a new paradigm, a game-changer. Our aim is to build the most crucial infrastructure and services with privacy as the foundation, thereby enabling the emergence of a monumental movement known as Web3. This is the essence of YourD service.

We have identified three fundamental components for constructing Web3 services: **prove, own, and apply**. These components must remain distinct. YourD encompasses the prove and own aspects, empowering individuals to validate and assert their ownership.
## Goal
We will **ignite a revolution in digital data ownership**, which will be the cornerstone of the forthcoming Fourth Industrial Revolution and the fundamental rule of the digital world going forward 
## YourD DID Identifier Syntax
- **DID Method Name**: YourD<br>
- **DID Method Specific Identifier**: We provide a DID (Decentralized Identifier) specification identifier based on blockchain accounts.<br>
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
```json
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
## CRUD Operation 
### Create/Register
The YourD DID JavaScript library enables the creation of Decentralized Identifiers (DIDs). The generated DID and associated DID Document are stored within the YourD application. Upon creation of a DID, relevant metadata is registered on the blockchain. This metadata, preserved on the blockchain, allows for the verification of the integrity of the DID Document during data access or updates.

### Read
The YourD DID method supports two functionalities: resolver and dereferencer.
- `resolve`: The resolver's resolve function permits holders to access their DID Documents held in the private data registry via their YourD DID. This function embodies the read operation on the decentralized identity infrastructure, aligning with the guidelines set forth in the W3C DID Specification. This ensures secure and standardized access to individual DID Documents, further cementing the decentralized nature of identity management facilitated by the YourD DID method.
- `derefererence`: The dereference functionality provided by YourD allows for retrieval of specific property values from the YourD DID Document through a DID URL. For instance, a specific value such as the service endpoint from the service attribute within a holder's DID Document can be obtained.
### Dereference Example
```json
{
   "dereferencingMetadata":{
      "contentType":"application/ld+json"
   },
   "contentStream":{
      "resource":{
         "data":"https://agent.example.com?service=files&relativeRef=%2Fmyresume%2Fdoc%3Fversion%3Dlatest#frag",
         "type":"ServiceEndpoint"
      }
   },
   "contentMetadata":{
      "created": "2023-04-19T02:16:00Z",
      "updated": "2023-04-19T02:16:00Z"
   }
}
```
### Update
A holder can update their DID Document located in the personal data registry through the YourD application. However, when updating the DID Document, it is essential to update the associated metadata on the related blockchain. Any alterations made to the DID Document without a corresponding metadata update on the blockchain are considered invalid by the YourD related DID services.
### Delete 
A holder has the ability to delete their DID Document from the private data registry. However, upon deletion of the DID Document, it is necessary to update the metadata on the blockchain network to deactivate the DID.

## Privacy / Security Consideration
At the heart of YourD's development process lies a robust commitment to privacy and security, anchored firmly within the guidelines set by the DID Specification. Recognizing the potential risks and scalability issues that could surface from uploading DID Documents onto the blockchain, YourD has taken a strategic approach.

Given that the upload of personally identifiable information, such as a service endpoint to a blockchain, poses a significant risk of irreversible data leakage, and could infringe on principles like GDPR's "right to be forgotten", YourD developed an alternative. To mitigate these concerns and provide a secure and accessible environment for users to manage their personal information, YourD offers a private data registry in the form of a YourD application, available on mobile and PC platforms.

YourD's application provides a secure storage facility, or 'lock', safeguarded with AES encryption, for DID Documents and derivative data. To bolster access security, YourD integrates biometric authentication measures, such as facial recognition or fingerprint scanning, for mobile devices.

To ensure users can receive verifiable credentials from trusted Issuers, YourD implements QR code functionality via pre-registered services. Additionally, when submitting verifiable presentations, identifiers are kept secret using zero-knowledge proofs, ensuring sensitive information remains confidential. This approach underscores YourD's commitment to privacy and aligns with the DID Specification's emphasis on user privacy and security.
## Reference
[Decentralized Identifier Resolution (DID Resolution) v0.3](https://www.w3.org/TR/did-core/)<br>
[DID Specification Registries](https://www.w3.org/TR/did-spec-registries/)<br>
[Verifiable Credentials Data Model v1.1](https://www.w3.org/TR/vc-data-model/)<br>
