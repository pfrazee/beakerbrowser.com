---
title: Dat files protocol
section: insideBeaker
sectionTitle: Inside Beaker
order: 1
---

Dat is a peer-to-peer protocol for exchanging archives of files. It is:

- **Secure.** Data is encrypted upon transfer and the content is verified on arrival. This prevents third-party access to metadata and content.
- **Transparent.** Changes to data are written in an append-only log, creating a version history that improves transparency and auditability.
- **Distributed.** With the Dat protocol you connect directly to other users or servers sharing or downloading common datasets. Any device can host files to share without the need for centralized servers.
- **Future-proof.** Unique links are generated using a public key and thus can be used instantly and forever to verify the dataset from anywhere.
- **Fast.** Files download from multiple sources. Quickly sync updates by only downloading the new bytes, saving time and bandwidth.

Dat’s primary use-case is to represent “data sources.” Archives are identified by public keys, and updates to the archives are synced by a background swarm process.

In Beaker, a Dat archive acts as a website. The public-key serves a similar purpose as an IP address in HTTP/S URLs; it is the domain which identifies the site. Dat URLs are formed as `dat://{publickey}/{path…}`, where the `publickey` is a 64-character, hex-encoded string.

Dat uses the public-key both to identify the archive, and as a symmetric key to encrypt the network traffic. In the discovery networks, a hash of the public-key is used to advertise the archive’s availability. Therefore, the Dat URL acts as a read-capability. An outside observer must know the public key of an archive to read its network traffic. 

Internally, Dat uses an append-only log which was inspired by Certificate Transparency and Secure Scuttlebutt. The log is addressed as a flattened merkle tree, which enables efficient exchange of the log history. By comparing the head-hashes of the log’s merkle-tree, peers can detect when the author of an archive has attempted to modify history. Because a divergent history could be used to send targeted malicious payloads, a modified history is considered a corruption event, and peers will reject the updates. This feature, we believe, makes Dat suitable for distributing software and security keys, as it enforces uniform distribution to the network.

Dat’s internal logs enable history archival and versioned reads. Using the log sequence numbers, it will be possible to create versioned URLs such as `dat://{pubkey}+{version}/{path…}`. For software modules and Web apps, this can be an extremely valuable feature. Because of the uniform-distribution of Dat histories, a versioned Dat URL is effectively static, similar to a hash-address.