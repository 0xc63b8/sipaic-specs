# SIPAIC Specification

Welcome to the official specification repository for **SIPAIC (Simple Internet Protocol Address Information Center)**. This repo defines the structure and rules for SIPAIC’s custom binary database formats designed for high-efficiency storage, and querying of IP-related data such as:

- IPv4 / IPv6 block allocation
- Country and RIR metadata
- ASN and routing information
- Fast lookups with binary parsing

This spec powers the core SIPAIC system and is versioned under the `/specs/v1` directory.

---

## What is SIPAIC?

SIPAIC is a lightweight, efficient, custom binary-based db format service that provides lookup and processing for IP-related information such as:

- ASN and Country allocations
- IP block  and Country allocations
- **Custom binary DB format (`.sipaicdb`)** for storing IP block, ASN, and network data.
- High-efficiency parsing and querying for IPv4/IPv6 and ASN records.

The binary format is optimized for fast reads, low memory overhead, and can be integrated into custom tools and services.

> Note: This repository focuses **only on the specifications** of the binary format used in SIPAIC releases.

---

## Who is this for?

- Developers writing **parsers or readers** for `.sdb` files
- Contributors maintaining or proposing extensions to the SIPAIC format
- Systems integrating SIPAIC into their infrastructure or services

---

## Key Concepts

- **Start Line**: Identifies version, file type, and row count
- **Headers Section**: Key-value metadata describing the file (e.g., data fields, generated date)
- **Data Records Section**: Binary-encoded rows with typed fields (e.g., IP start, count, country code)
- **Endianness**: All integers are stored in **big-endian** by default

---

## Structure

```dir
sipaic-specs/
 ├── specs/ # Versioned specifications
 ├── glossary.md # Defined terminology
 └── CONTRIBUTING.md # Proposals & contribution guidelines
```

---

## Contribution Policy

This specification is tightly coupled to the SIPAIC service design. As such, we do not accept external contributions. See [CONTRIBUTING.md](./CONTRIBUTING.md) for more details.

---

## License

This specification is open-sourced under the [MIT License](./LICENSE).
