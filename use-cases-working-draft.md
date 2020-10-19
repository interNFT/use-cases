---
Working Draft for Comment / Interchain Standards for NFTs & Metadata
---

# Use Cases and Requirements

## Abstract

Non-Fungible Tokens are containers for uniquely identified resources, which are represented by NFT metadata. NFTs enable rights of ownership and control over resource identifiers. They may also contain other rights, within specific contexts and use-case.

By developing Interchain Standards for NFTs and Metadata, we intend to make NFTs interoperable across blockchain networks and to enable ownership and control of NFT metadata and linked resources, regardless of where these are located across blockchain networks, the web, or offline. 

Interchain NFTs and Metadata should have features which will directly benefit users, promote the adoption of decentralised web standards and offer new economic mechanisms for sustainable digital finance and the impact economy.

By presenting a set of canonical use-cases and user stories, this document starts to describe the defining features of Interchain NFTs and Metadata, and why these are beneficial. 

This document is intended to support the InterNFT Working Group to identify technical requirements for developing an interface standard for Interchain NFTs and an Interchain Metadata Standard for NFT referent resources. Recommendations in these standards should be sense-checked against these use-cases and requirements.

This is a living document which will remain in a “working-draft” state, to encourage further contributions, improvements and addition on new use cases, examples and user stories.

## Status of this Working Draft Document

_This section describes the status and current Git Version of this document. Other documents may supersede this document._

This is a draft which may be updated, replaced or made obsolete by new versions at any time. Only cite this as a work in progress.

The document is being developed by the [Working Group for Interchain Non-Fungible Tokens and Metadata](https://internft.org).

The use case model and specific examples described here are not intended to be exhaustive or complete. Rather, this is intended to capture a broad understanding of the problem space and the generic requirements which need to be considered when drafting standards for NFTs and Metadata. The technical concepts and experiences in implementing various of these concepts are still nascent and are likely to significantly evolve. By sense-checking these concepts against real-world use cases and requirements, this work can remain both relevant and focused.

[GitHub Issues](http://tbc/) are preferred for discussion of this specification. Changes may be proposed as Github Pull Requests.

## Terminology

| Authentication | A process which is defined by a protocol for an entity to prove it has a specific attribute or that it controls a specific secret, using one or more [verification methods](https://www.w3.org/TR/did-use-cases/#dfn-verification-method). |
| :--- | :--- |
| Assertion | A statement by an identified party, with or without implicit or explicit guarantees as to its validity, or authenticity of the identity of the party. |
| [Content Address](https://docs.ipfs.io/concepts/content-addressing/) | A method for identifying a resource using the content of the resource, which is typically formed by cryptographic hashing |
| Consensus | A standardised process for the participants in a [network](https://objectcomputing.com/expertise/blockchain/glossary#network) to determine a single truth, in the context of blockchain protocols |
| CID | Content address as specified by the [Interplanetary File System \(IPFS\) protocol](https://ipfs.io) |
| Data Format Specification | An agreement on the correct interpretation of [representation](https://www.w3.org/TR/webarch/#def-representation) data |
| [Decentralised Identifier](https://www.w3.org/TR/did-core/) \(DID\) | A globally unique persistent identifier for any subject \(person, organization, thing, data model, abstract entity, etc.\) that does not require a centralized registration authority because it is generated and/or registered cryptographically |
| [DID Document](https://www.w3.org/TR/did-core/) | The metadata for a resource which is identified by a decentralised identifier |
| Fungible | Things that are equivalent or part of an identical set of things, which makes them interchangeable |
| Hash | Cryptographic hashes are functions that take some arbitrary data input and return a fixed-length value, which is determined by the specific hash algorithm used |
| [Internationalised Resource Identifier](https://en.wikipedia.org/wiki/Internationalized_Resource_Identifier) \(IRI\) | The international version of a Universal Resource Identifier \(URI\), which allows for the use of additional character sets |
| IRI Owner | By convention, the entity who gets to say what the intended \(or usual\) referent is for an [IRI](https://www.w3.org/TR/rdf11-concepts/#dfn-iri) |
| Label | A set of assertions with a common implicit subject _\(attribute-value pairs linked to an identifier for the subject\)_ |
| Links | An assertion of relationship between two resources |
| [Linked-Data](https://www.w3.org/TR/ld-glossary/#linked-data) | A pattern for hyperlinking machine-readable data sets to each other, in ways that are also understandable by humans, using Semantic Web standards |
| Metadata | Machine understandable information about web resources or other things |
| Non-Fungible | Things that are uniquely identifiable individually, or as part of a set of things which are not equivalent, which makes them not interchangeable |
| Referent | The [resource](https://www.w3.org/TR/rdf11-concepts/#dfn-resource) [denoted](https://www.w3.org/TR/rdf11-concepts/#dfn-denote) by an [IRI](https://www.w3.org/TR/rdf11-concepts/#dfn-iri) |
| [Representation](https://www.w3.org/TR/webarch/#def-representation) | Information about a past, current, or desired future state of a resource, in a data format that can be readily communicated and understood with metadata. Representations do not necessarily describe the actual resource, or portray a likeness of the resource, or represent the resource in other senses of the word "represent". \(As defined by [RFC7231](https://www.w3.org/TR/did-use-cases/#bib-rfc7231)\) |
| Resource | Any identifiable thing. Including physical things, documents, digital objects, abstract concepts, numbers and strings. “Anything that may be identified by a URI” \(As defined by [RFC3986](https://www.w3.org/TR/did-use-cases/#bib-rfc3986)\) |
| State | A computational model which represents one of a finite set of possible states at a given point in time, which cannot be reversed and which enforces a state transition process to change at the state at a subsequent point in time |
| Token | A container of information which is controlled by a cryptographic secret key |
| Universally Unique Identifier \(UUID\) | A type of globally unique identifier that does not require a centralized registration authority, but \(unlike DIDs\) is not resolvable or cryptographically verifiable. \(As defined by \([RFC4122](https://www.w3.org/TR/did-use-cases/#bib-rfc4122)\) |
| Validation | Mathematically proving that a value is valid, in the context of cryptographic protocols |
| Verification | Evaluation of a claim to determine if it is valid, authentic, conforms to a required standard specification, and satisfies a defined cryptographic proof method |
| Verifiable Claim | An assertion about a subject, made by an identified entity who can be authenticated, which can be verified based on a set of standard requirements and cryptographic proofs |

# 1. Introduction

Tokenizing real-world resources is a critical enabler for the digital economy. This is also essential for transitioning the world to more accountable, sustainable means of producing and using natural resources.

It is now technically feasible for any uniquely identifiable physical world resource — whether tangible or intangible, to be represented in a non-fungible tokenized digital format.

Non-fungible Tokens \(NFTs\) have powerful features, such as embedded rights, provenance and verifiability. The range of canonical use-cases and list of potential features of NFTs and Metadata are growing.

An interoperable NFT and metadata standard is necessary for tokenized digital resources to be virtually addressed, described, authenticated, controlled or exchanged across blockchain networks and through the Web.

This document sets out use cases and requirements for establishing standards which could be adopted to achieve interoperability between blockchain networks, which will be compatible with long-established Internet standards and which build on the latest decentralised web specifications.

> _“Throughout the World Wide Web, as trust becomes an important issue, it will be important for software -- and people -- to keep track of and take into account who said what in terms of data and metadata”. Tim Berners-Lee \(1997\)_

### Core characteristics of Interchain NFTs & Metadata

Cryptographic tokens which subscribe to the Interchain Standards for NFTs & Metadata are characterised as being:

1. **Uniquely identifiable** so that instances cannot be duplicated or copied without detection;
2. **Ownable** with associated rights and capabilities which can only be transacted and transferred by the owner/s of the asset;
3. **Resolvable** to enable discovery, validation and verification of assertions and their linked resources;
4. **Decentralised** with no requirement for a central issuing agency;
5. **Persistent** to not be reliant on the custodianship or continued operation of organisations which are impermanent;
6. **Cryptographically verifiable** to prove that assertions and resources have not become corrupted and to demonstrate control over authenticated resource identifiers;
7. **Stateful** to establish a sequential order in which a metadata and resources are recorded, for provenance as well as temporal and relational integrity.

Other classes of tokenized assets and resources may display some of these characteristics, but cannot be described as _Interchain NFTs_, if they do not display all of these characteristics.

### The concept of a Non-Fungible Token

A Non-Fungible Token \(NFT\) is a container for identifying a unique resource. It may also contain rights associated with the resource. The token owner has the ability to change this representation of the resource.

NFTs are not interchangeable, as each token can have a different value to other tokens within the same set.

### The concept of Metadata relating to NFTs

NFT Metadata is a set of assertions which describe one or more uniquely identified resources that are referent to an NFT.

#### Digital resources

A _Resource_ is any identifiable thing. This includes physical things, documents, digital objects, abstract concepts, numbers and strings. in the context of the Internet a resource has historically been defined as “The thing which you get when you follow a link”.

In the context of NFTs, a resource could be a natively digital object, such as a digital artwork, or information which is linked to physical objects, such as a digital certificate that contains assertions about a specific section of land.

#### Metadata

Information about a resource is described as metadata. This typically asserts one or more sets of attributes about the resource. These attributes are usually key-value pairs. The [_Resource Description Framework_](https://www.w3.org/RDF/) is a well-established pervasive standard for describing resource attributes in the context of the Web. However, this metadata does not maintain a globally consistent state and is mutable.

A standardised format for NFT Metadata has not yet been established. For NFTs metadata to become interoperable, we need a description standard which can be interpreted and understood across different contexts, locations and technology implementations.

> _"URI persistence is a matter of policy and commitment on the part of the URI owner. The choice of a particular URI scheme provides no guarantee that those URIs will be persistent or that they will not be persistent."_ [_W3C,_](https://www.w3.org/TR/webarch/#def-representation) [_2004_](https://www.w3.org/TR/webarch/#def-representation)

#### Unique instances of digital resources

There is currently no standard way to identify the uniqueness of resources across different namespaces.

A Universal Resource Locator \(URL\) identifies a unique instance of a web resource at an address within a namespace. However, this does not guarantee uniqueness of the resource, as this may be duplicated at multiple locations.

With cryptographic hashes, resource metadata and instances of resource data can establish an immutable, unique identity for a resource. A variety of hash algorithms could be used for this purpose. Resolving the identity of a Resource requires knowledge of which specific hash algorithm was used. There is currently no broadly adopted standardised way to achieve this resolution, but the IPFS specification for Content Addresses \(CID\) is gaining adoption.

An Interchain standard for NFT metadata should aspire to address and authenticate the uniqueness of a resource across all distributed ledger namespaces.

#### The state of digital resources

The sequential order and time of recording resource metadata matters for provenance, temporal and relational integrity. When hashes of resource metadata and/or data are committed to a [Merkle Tree](https://en.wikipedia.org/wiki/Merkle_tree), these resources maintain state within the context of a directed acyclic graph. If this graph is committed to the state of a distributed ledger, the resource maintains a unique state in the context of the ledger namespace.

#### Classes of resources

A classification system for resources should enable us to distinguish differences between canonical classes of resources, which can be linked to exemplary use-cases. This will allow us to identify differences in requirements and features for each unique class, which must be taken into consideration for the design of an Interchain standard.

The [Interwork Alliance](https://interwork.org/) has introduced a [Token Taxonomy](https://github.com/InterWorkAlliance/TokenTaxonomyFramework/blob/master/token-taxonomy.md) which describes a classification hierarchy for tokens that proposes a standard [Taxonomy Model](https://github.com/InterWorkAlliance/TokenTaxonomyFramework/blob/master/taxonomy-model.md) for representing classes, properties and behaviours of tokens in structured data templates.

###  The purpose of Interchain Standards

Interchain Standards for NFTs should provide an interoperable, standard way to own, authenticate and transact with non-fungible tokens across blockchain networks.

Interchain standards for NFT metadata should make information about the resources which are linked to NFTs machine-readable, machine understandable and verifiable, regardless of where this metadata is located, across blockchains, the web, or offline.

Together, these standards will unlock the potential for NFTs and their metadata to become as pervasive and interoperable as URLs are on the web. This will provide a significant renovation to the architecture and utility of the web, by providing stateful and verifiable representations of unique web resources.

### Existing Work

#### NFTs

[KryptoKitties](https://www.cryptokitties.co/) is the first widely-known example of Non-Fungible Tokens. When this launched in November 2017, it introduced a mechanism for creating and owning unique digital resources that people desire as collectibles. This was based on a technical specification \([ERC-712](https://github.com/ethereum/EIPs/issues/721)\) for the minimum interface that a smart contract on the Ethereum network must implement to allow unique tokens to be created, managed, owned, and traded. This specification does not mandate a standard for token metadata or restrict adding supplemental functions.

Subsequently a number of new ethereum network specifications have been proposed to add supplemental functions and enhancements to the ERC-712 standard. These include methods for combining fungible and non-fungible tokens in multi-token transactions \([ERC-1155](https://github.com/ethereum/EIPs/issues/1155)\), to delegate ownership and control \([ERC-994](https://github.com/ethereum/EIPs/issues/994)\), compose NFTs into hierarchical ownership schemes \([ERC-998](https://github.com/ethereum/EIPs/issues/998)\), for fractional ownership of NFTs \([ERC-1633](https://github.com/ethereum/EIPs/pull/1633)\) and other innovations.

Although there is no single standard for NFTs across different blockchain networks, ERC-712 provides the canonical definition for an NFT interface standard.

####  Metadata

There are various well-established formats for describing and processing metadata about digital resources. The most widely adopted is the [Resource Description Framework](https://www.w3.org/RDF/) \(RDF\). Mainstream translations of this framework have been made into programming languages such as Javascript \(JSON\).

Metadata properties are becoming standardised in open schemas, such as [schema.org](https://schema.org/), which enables information about web resources to be structured in a way that is semantically understood and machine-readable. With [linked-data](https://www.w3.org/wiki/LinkedData) models, such as [JSON-LD](https://json-ld.org/), metadata is becoming more structured and graph-based.

This means that now when we describe a resource, such as a _dataset_, in its context of [schema.org/dataset](https://schema.org/Dataset), everyone can have a shared understanding of what is represented by the resource description.

This approach can be used to describe any conceivable representation of a resource. We should also be able to localise resource descriptions, for these can be widely understood, regardless of a user’s language.

# 2. Use Cases

Each use-case presents the canonical form of a non-fungible token and the types of resources the token metadata describes. A comparison with legacy ways of describing and using resources helps illustrate the distinctive properties of these tokens and how these enable applications to be built which have not previously been possible. Examples are provided as links, which the link owner may choose to describe in their own terms, using their own resources.

Note: These use-cases and examples are not exhaustive and are only intended to provide a high-level overview for an initial scope of requirements for drafting Internachain NFT and Metadata standards. This list of use-cases and examples is expected to grow. Naming use-case as types of NFTs suggests a taxonomy for NFT classes of NFTs. This taxonomy should further evolve, as the use cases are populated with new examples and as new use-case classes are discovered which don’t fit this initial list.

### 2.1 Collectible Tokens

Collectible Tokens contain unique digital objects which people desire to own. These tokens enable control over the digital objects and infer rights of ownership and usage. Owning a digital collectible may confer further rights and capabilities within a specific system, or across systems such as virtual gaming worlds.

Collectible Token metadata may be self-describing, with the digital object being the same as the metadata resource, or it may describe a digital resource which can be accessed within a specific domain space. Digital Collectibles were the original conception of Non-Fungible Tokens.

Digital collectible objects have physical world analogies in the form of collectibles such as baseball cards, but the virtual universe of digital objects is much larger and more diverse.

  
Tokenizing collectible digital objects enables these to be owned and traded in virtual marketplaces. Collectible Tokens are being used in an increasing range of virtual world games and simulations. New and secondary sales of digital collectibles are generating valuable new online marketplaces.

Examples: [Cryptokitties](https://www.cryptokitties.co/),

### 2.2 Financing Tokens

Financing Tokens contain real-economy financial claims and agreements. These may be associated with rights of payment for the delivery of commodities and services, and rights to receive these as agreed.

The metadata associated with Financing Tokens describes financial claims and related documents, such as invoices, delivery notes and receipts.

Tokenizing financing enables the documentary evidence and associated rights associated with financing deals to be used as collateral for securing capital loans and to issue payment guarantees.

Examples: [Centrifuge](https://centrifuge.io/), [Persistence One](https://persistence.one/),

### 2.3 Impact Tokens

Impact tokens contain proofs about the social, environmental and economic state of the world. These tokens have intrinsic value linked to verifiable claims, outcome payments, executable rights and data assets. Impact tokens of various types may be issued, sold and traded as digital commodities. Carbon Credit Tokens are an example of Impact Tokens which are issued on the basis of verified Carbon Emission Reduction claims.

Impact Token metadata describes the information which is used to measure, verify and report on impacts. This is recorded in a stateful graph for comparing and attributing impacts over time, relating impacts across systems and to represent desired future state outcomes.

Legacy mechanisms for recording claims of impact mostly use analogue methods, with reliance on trusted intermediaries to generate documentary reports. Some types of impact are recognized by central authorities who issue certificates that are referenced in centralised registries and traded over-the-counter.

Tokenizing impact claims and their verification proofs makes it possible to more precisely account for and place economic value on impacts. This provides critical information for financing and implementing all types of interventions for sustainable development, ecological regeneration and mitigating climate change.

Examples: [ixo](https://ixo.foundation/), [Regen Network](https://www.regen.network/),

### 2.4 Access Tokens

Access Tokens contain rights to use proprietary physical or virtual resources for specified purposes. These rights may be transferable or non-transferable, perpetual or time-limited.

The metadata of an Access Token describes a proprietary resource and its associated terms of use. It may include a digital key that removes usage restrictions or provides authorisation.

Legacy mechanisms to access proprietary resources are typically dependent on intermediary processes to assign, transfer and operationalise rights of usage, based on terms such as membership, ownership and rental. Digital locks for virtual resources and embedded into physical objects now make it possible to virtualise, embed logic and build financial transactions into all types of access mechanisms.

Tokenizing access rights makes it possible to distribute access rights in more targeted, decentralised and distributed ways. Access may be created or restricted for more types of resources. This can impose limitations on unsustainable over-use of resources, or expand the possibilities of how resources can be shared and used most optimally.

Examples: [IrisNet](https://www.irisnet.org/), [Decentraland](https://decentraland.org/),

### 2.5 Art Tokens

Art Tokens contain the rights to a registered patent or copyright material. These rights may be protected by intellectual property laws.

Art Token metadata describes the art, which may be patented or copyright physical or virtual materials, together with associated licenses and claims.

{Legacy IP assets}

Tokenizing art makes it possible to determine its provenance, trade ownership of art \(with or without physical transfers\), finance the creation of new art or inventions and to license the use of this property in a wider range of applications.

 Examples: [Left Gallery](https://left.gallery/), [Molecule](http://www.molecule.io/)

### 2.6 Physical Property Tokens

Physical Property Tokens contain digital representations of physical-world objects and resources. They may infer rights of ownership, control and usage of physical property.

Physical Property Token metadata describes the physical property and digital representations of this property, with links to related documentation such as title deeds, certificates of ownership and other claims about the property. Digital representations of physical property may be linked by embedded identifiers, such as decentralised identifiers, unique serial numbers and biometric identifiers.

Legacy forms of representing physical property include physical or electronic certificates and title deeds, which may be difficult to authenticate and are susceptible to forgery, duplication and loss of records.

Tokenizing physical property makes this available to be used in digital transactions, as collateral and for new types of derivative products and services. Proof of ownership and fractionalised ownership are more feasible. The transaction costs and administrative time of transferring ownership may be dramatically decreased. The provenance, credentials and chain of custody of physical property can be proven. All types of verifiable claims and rights may be associated with the property. Tokenization may reduce counterfeiting by enabling more robust identification and authentication of physical property. It provides new ways of communicating about and organising the use of physical property. This is seen as an important enabler for the sharing economy.

Examples: [Mattereum](https://mattereum.com/),

### 2.7 Data Tokens

Data Tokens contain data assets. These tokens are associated with rights of ownership of data assets and the licenses to use these assets for specific purposes.

Data Token metadata describes data resources, with information about the location and access rights to the data.

Legacy data storage and retrieval systems restrict access and usage of data, to ensure data security and privacy. This traps valuable data in silos and has also had the effect of centralising control and ownership of data by large corporations which have the commercial and technological powers to source, store and process large amounts of data.

Tokenizing data assets makes it possible to create new types of data marketplaces for securely sharing data assets, with automated access control mechanisms. This should democratise market participation and access to big data, which is particularly important for building artificial intelligence capabilities which are not exclusively controlled by large corporations.

Example: [Ocean Protocol](https://oceanprotocol.com/)

### 2.8 Credential Tokens

Credential Tokens contain verifiable claims about the identity and attributes of a subject. The issuers of these claims can be identified and authenticated. The subject of a credential token may have certain rights in specific contexts, which are not available without the credential.

Credential Token metadata describes one or more verifiable claims about an identified subject.

Legacy credential systems require trusted issuers of credentials to maintain a persistent central registry of information which relying parties can access. Analogue or digital credential certificate documents have traditionally been used to represent and operationalise the rights associated with credentials.

Tokenizing credentials enables identity and rights associated with having certain attributes to be authenticated and used in a wider range of physical and virtual contexts.

Examples: [Starname](https://starname.me)

### 2.9 Capability Tokens

Capability Tokens contain electronic rights within software systems. These tokens transfer Object Capabilities, which are authorisations to perform restricted scopes computational processes that get executed at the level of a software operating system.

Capability Token metadata describes object capabilities in object-oriented code.

Legacy software systems do not restrict at a granular level the scopes of computational processes or authorisations which can be implemented across non-concurrent systems. This creates security vulnerabilities and limits the capability to communicate and execute code across systems.

Tokenizing capabilities makes it possible to own a unique object capability and to transfer ownership and/or control of the rights which are associated with this. It makes possible {...tbc}.

Examples: [Agoric](https://agoric.com/)

### 2.10 Commodity Tokens

Commodity Tokens contain information about the identity and origin of commodities.

Tokenizing commodities enables consumers to verify the provenance of a commodity and increases transparency in the commodity supply chain.

{...tbc}

Examples: [Provenance](https://provenance.org), 

# 3. Requirements

The canonical use-cases for NFTs and Metadata have a set of common business and technical requirements. Each use-case relies on a subset of these requirements to be met.

The requirements for Interchain NFTs include that these should be:

1. **Mintable** to issue new tokens of the same class to a token set.
2. **Burnable** to remove tokens from the token set.
3. **Ownable** to control the token metadata using a private key.
4. **Transferable** to change ownership.
5. **Non-transferable** to not permit changes in ownership.
6. **Lockable** to conditionally stop changes in the token metadata.
7. **Immutable** to never permit changes in the token metadata.
8. **Mutable** to unconditionally permit changes in the token metadata.
9. **Re-fungible** to mint fungible tokens which represent interchangeable units of information.
10. **Divisible** to allow fractional ownership of non-fungible parts.
11. **Composible** to be owned by another non-fungible token and added to that token’s set or to produce other novel combinatorial forms.
12. **Conditional** to only permit changes or transfers when specific conditions have been met.

|  | **Requirements** |  |  |  |  |  |  |  |  |  |  |  |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Use-Case** | **1** | **2** | **3** | **4** | **5** | **6** | **7** | **8** | **9** | **10** | **11** | **12** |
| Collectible Tokens | X |  | X | X |  | X | X | X | X |  |  |  |
| Financing Tokens | X | X | X | X | X | X | X | X | X | X | X | X |
| Impact Tokens | X | X | X | X | X | X | X |  | X | X | X | X |
| Access Tokens | X | X | X | X | X | X | X | X | X | X | X | X |
| Art Tokens | X |  | X | X |  |  | X | X | X | X | X | X |
| Physical Property Tokens | X | X | X | X | X | X | X | X | X | X | X | X |
| Data Tokens | X | X | X | X | X | X | X | X | X | X | X | X |
| Credential Tokens | X | X |  | X | X |  | X |  |  |  | X | X |
| Capability Tokens |  |  |  |  |  |  |  |  |  |  |  |  |
| Commodity Tokens | X | X | X | X | X | X | X | X | X | X | X | X |
|  |  |  |  |  |  |  |  |  |  |  |  |  |

# 4. User Stories

{% hint style="info" %}
Projects are invited to describe their use-case in the format of a short User Story. This must emphasise the unique challenges and distinctive requirements which must be met by the Interchain Standard for NFTs and Metadata. This includes edge-cases which can be helpful for testing the validity and potential limitations of these standards. To propose new user stories by submitting a Github Pull Request on this document.
{% endhint %}

### 4.1 Quality Carbon Credits

#### Context

#### User Needs

#### Unique Challenges

#### Distinctive Requirements

### 4.2 Financing commodity trade deals

#### Context

#### User Needs

#### Unique Challenges

#### Distinctive Requirements

### 4.3 Crowd-sourced funding for Pharmaceutical Patents

#### Context

#### User Needs

#### Unique Challenges

#### Distinctive Requirements

### 4.4 Primary Education Impact Bond

#### Context

#### User Needs

#### Unique Challenges

#### Distinctive Requirements

### 4.5 Private Credentials

#### Context

#### User Needs

#### Unique Challenges

#### Distinctive Requirements

### 4.6 Blockchain Transaction Receipts

#### Context

#### User Needs

#### Unique Challenges

#### Distinctive Requirements

# 5. References



