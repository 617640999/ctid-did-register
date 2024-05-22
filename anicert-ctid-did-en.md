# CTID DID Method Specification

versionId 1.0.0

## About

This DID method specification  conforms to the requirements in the DID specification currently published by the W3C Credentials Community Group. For more information about DIDs and DID method specifications, please see the [DID Spec](https://w3c.github.io/did-core/). 

The following DID Method will be registered in the [DID Specification Registries](https://w3c.github.io/did-spec-registries/#did-methods).

## Abstract

CTID Digital Identity Chain, a new infrastructure for distributed digital identity applications, aims to provide authoritative, trustworthy, secure, and convenient distributed digital identity authentication services, which is managed by Beijing Zhongdun Anxin Science and Technology Development Co., Ltd. CTID DID method generates digital identity identifiers and verifiable credentials to provide distributed digital identity services for various industries.

## Status of  This Document

This document was published as an Editor's Draft. 

Publication as an Editor's Draft does not imply endorsement by the W3C Membership. This is a draft document and may be updated, replaced or obsoleted by other documents at any time. It is inappropriate to cite this document as other than a work in progress. 

## CTID DID Method

- The namestring that shall identify this DID method is : ctid 


- A DID that uses this method MUST begin with the following prefix: did:ctid. According to the [DID specification of Syntax](https://www.w3.org/TR/did-core/#did-syntax), this string MUST be in lowercase. The remainder of the DID, after the prefix, is the MSI specified below. 

### Method Specific Identifier (MSI) 

Method Specific Identifier (MSI) generation rule：

- Using SM3, the national commercial cryptographic algorithm of the People's Republic of China, the personal identity attribute is hashed and the hash value is obtained.
- Convert the hash value to hexadecimal (uppercase).

```
    method-specific-id = <hexdigit>{64}
    hexdigit = [0-9A-F]
```

Examples:
```
    did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073
```
## DID Document
```
{
	"@context": "https://www.w3.org/ns/did/v1",
	"id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
	"versionId": "v1", 
	"created": "2023-12-13T15:41:01Z",  
	"update": "2023-12-26T17:16:08Z",   
	"authentication": [{
		"id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-1",
		"type": "sm2p256v1",
		"expirationDate": "",
		"publicKeyHex": "044e801f22a5bc5c4a672800b78677fcff9a2d05864d772397e4cb3552b0ea0f2dcb367ec741b3c639f8b47b53bbf449036423bfcd4c4dabe74171599af16802a6"
	}, {
		"id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-2",
		"type": "sm2p256v1",
		"expirationDate": "",
		"publicKeyHex": "04a3d297fe2ad2699f87a2d5d9fc62403c8a63be0fbbe5890c41fa8e1c9c6409523c267ddb0bd12d6589c3b94099f0429413c3f6e63194e43dc13a5169b08a00f6"
	}],
	"service": [{
		"id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
		"type": "",
		"serviceEndpoint": ""
	}],
	"proof": {
		"type": "sm2p256v1",
		"created": "2023-12-26T17:16:08Z",
		"creator": "did:ctid:anicert",
		"signatureValue": "3046022100a74a1639e3aad5b9333a49214a4ab89364fc310860cd08961c41deb80f5ef712022100d5de2d2fde7212e2fb19aea0bb75f57b9ebd55b6d64516d53df9ef81f397d985"
	}
}
```

## CTID DID Method Specification
### Create
To create a DID document, you must submit a transaction that looks like this: 

```
POST /didservice/v1/did/create  HTTP/1.1
Content-Type: application/ld+json
Accept: application/ld+json, application/json, text/plain, */*
Accept-Encoding: gzip, deflate

{
  "did":"did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
  "operate":"create",
  "doc": {
    "@context": "https://www.w3.org/ns/did/v1",
    "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
    "versionId": "v1",
    "created": "2023-12-13T15:41:01Z",
    "update": "2023-12-26T17:16:08Z",
    "authentication": [
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-1",
        "type": "sm2p256v1",
        "expirationDate": "",
        "publicKeyHex": "044e801f22a5bc5c4a672800b78677fcff9a2d05864d772397e4cb3552b0ea0f2dcb367ec741b3c639f8b47b53bbf449036423bfcd4c4dabe74171599af16802a6"
      },
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-2",
        "type": "sm2p256v1",
        "expirationDate": "",
        "publicKeyHex": "04a3d297fe2ad2699f87a2d5d9fc62403c8a63be0fbbe5890c41fa8e1c9c6409523c267ddb0bd12d6589c3b94099f0429413c3f6e63194e43dc13a5169b08a00f6"
      }
    ],
    "service": [
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
        "type": "",
        "serviceEndpoint": ""
      }
    ],
    "proof": {
      "type": "sm2p256v1",
      "created": "2023-12-26T17:16:08Z",
      "creator": "did:ctid:anicert",
      "signatureValue": "3046022100a74a1639e3aad5b9333a49214a4ab89364fc310860cd08961c41deb80f5ef712022100d5de2d2fde7212e2fb19aea0bb75f57b9ebd55b6d64516d53df9ef81f397d985"
    }
  }
}
```

### Read 

A DID Document can be read by performing an HTTP POST containing following elements.                                  

To query a DID document, you must submit a transaction that looks like this:

```
POST /didservice/v1/did/get  HTTP/1.1
Content-Type: application/ld+json
Accept: application/ld+json, application/json, text/plain, */*
Accept-Encoding: gzip, deflate

{
    "did": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073"
}
```

To read an identifier, look it up from the blockchain, and then directly obtain the DID document, for example:

```
{
  "code":"200",
  "msg":"ok",
  "txid": "236357c77285355f64b99b2ac2a1f…",
  "blockHeight": 155522625,
  "doc": {
    "@context": "https://www.w3.org/ns/did/v1",
    "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
    "versionId": "v1",
    "created": "2023-12-13T15:41:01Z",
    "update": "2023-12-26T17:16:08Z",
    "authentication": [
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-1",
        "type": "sm2p256v1",
        "expirationDate": "",
        "publicKeyHex": "044e801f22a5bc5c4a672800b78677fcff9a2d05864d772397e4cb3552b0ea0f2dcb367ec741b3c639f8b47b53bbf449036423bfcd4c4dabe74171599af16802a6"
      },
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-2",
        "type": "sm2p256v1",
        "expirationDate": "",
        "publicKeyHex": "04a3d297fe2ad2699f87a2d5d9fc62403c8a63be0fbbe5890c41fa8e1c9c6409523c267ddb0bd12d6589c3b94099f0429413c3f6e63194e43dc13a5169b08a00f6"
      }
    ],
    "service": [
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
        "type": "",
        "serviceEndpoint": ""
      }
    ],
    "proof": {
      "type": "sm2p256v1",
      "created": "2023-12-26T17:16:08Z",
      "creator": "did:ctid:anicert",
      "signatureValue": "3046022100a74a1639e3aad5b9333a49214a4ab89364fc310860cd08961c41deb80f5ef712022100d5de2d2fde7212e2fb19aea0bb75f57b9ebd55b6d64516d53df9ef81f397d985"
    }
  }
}
```

### Update

A DID document can be replaced by performing an HTTP POST containing following elements.

To update a DID document, you must submit a transaction that looks like this:

```
POST /didservice/v1/did/update  HTTP/1.1
Content-Type: application/ld+json
Accept: application/ld+json, application/json, text/plain, */*
Accept-Encoding: gzip, deflate

{
  "did":"did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
  "operate":"update",
  "doc": {
    "@context": "https://www.w3.org/ns/did/v1",
    "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
    "versionId": "v1",
    "created": "2023-12-13T15:41:01Z",
    "update": "2023-12-26T17:16:08Z",
    "authentication": [
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-1",
        "type": "sm2p256v1",
        "expirationDate": "",
        "publicKeyHex": "044e801f22a5bc5c4a672800b78677fcff9a2d05864d772397e4cb3552b0ea0f2dcb367ec741b3c639f8b47b53bbf449036423bfcd4c4dabe74171599af16802a6"
      },
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073#keys-2",
        "type": "sm2p256v1",
        "expirationDate": "",
        "publicKeyHex": "04a3d297fe2ad2699f87a2d5d9fc62403c8a63be0fbbe5890c41fa8e1c9c6409523c267ddb0bd12d6589c3b94099f0429413c3f6e63194e43dc13a5169b08a00f6"
      }
    ],
    "service": [
      {
        "id": "did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
        "type": "",
        "serviceEndpoint": ""
      }
    ],
    "proof": {
      "type": "sm2p256v1",
      "created": "2023-12-26T17:16:08Z",
      "creator": "did:ctid:anicert",
      "signatureValue": "3046022100a74a1639e3aad5b9333a49214a4ab89364fc310860cd08961c41deb80f5ef712022100d5de2d2fde7212e2fb19aea0bb75f57b9ebd55b6d64516d53df9ef81f397d985"
    }
  }
}
```

### Delete（Revoke）

Deletion means invalidation of the existing DID. An invalid DID has its revoked date time set;

```
    "revoked": "2020-01-01T23:59:00Z"
```

A DID document can be revoked by performing an HTTP POST.             


To revoke the document of the DID, the owner of the DID should send a request that looks like this:


```
POST /didservice/v1/did/del  HTTP/1.1
Content-Type: application/ld+json
Accept: application/ld+json, application/json, text/plain, */*
Accept-Encoding: gzip, deflate

{
    "did":"did:ctid:16D44117484372A2D010BDAA56703E723FB4C5C06CA44105F0C9C5B8020A7073",
    "operate":"delete",
}
```

## Security and Privacy Considerations
- All transactions are transmitted encrypted
- We will not include any personal data in the DID document
- The information related to the user's privacy is not linked, or on the authority side, the statement submitted by the authority is used to prove the user's proprietary attribute, so as to better protect the user's privacy from being replaced.
- It can be proved that the private key owned by the DID only exists on the user's device and will not be known to any third party.
- DID documents use signature technology to prevent malicious error correction.
