# SIPAICDB Specification v1

**SIPAICDB** (Simple Internet Protocol Address Information Center Database) is a custom binary file format for storing structured and efficient IP address information. This specification defines the version 1 format, including its structure, header requirements, data sections, supported field types, and expected formats.

---

## Table of Contents

1. [Overview](#overview)
2. [File Structure](#file-structure)
3. [Start Line](#start-line)
4. [Header Section](#header-section)
5. [Data Section](#data-section)
6. [Supported Field Types](#supported-field-types)
7. [Data Format Types](#data-format-types)
8. [Glossary](#glossary)

---

## Overview

SIPAICDB is a compact, cross-platform compatible binary format designed to deliver high-performance lookup and analytics for IP and network-related metadata. It is used by the SIPAIC system to store and distribute records such as IP allocations, country assignments, and regional registry (RIR) information.

All multi-byte integers are stored in **Big Endian** format. Each file includes a Start Line, followed by a fixed number of headers and a structured data section.

---

## File Structure

```txt
+---------------------------+
| Start Line (32 B)         |
+---------------------------+
| Header Section (64 B x N) |
+---------------------------+
| Data Section              |
+---------------------------+
```

---

## Start Line

The first 32 bytes of the file. It contains:

- Magic identifier
- Format version
- Number of headers
- Number of data records

> See [Start-Line.md](./Start-Line.md) for detailed field layout.

---

## Header Section

Each header is exactly 64 bytes and formatted as `Key:Value`. Headers define the structure of the data section and metadata about the file.

> See [Common-Header.md](./Common-Header.md) for full details.

---

## Data Section

Contains actual record rows. Each row has a fixed layout based on the headers. Fields are separated by null bytes (`\0`) for safe parsing and alignment.

> See [Data-Section.md](./Data-Section.md) for layout and parsing rules.

---

## Supported Field Types

SIPAICDB v1 supports a fixed set of field types, including integers, fixed-length strings, and timestamps.

> See [Field-Type.md](./Field-Type.md)

---

## Data Format Types

The `Data-Format` header specifies the type of data stored. Supported values include:

- `ipv4/country`
- `ipv4/rir`
- `ipv4/country-rir`
- `ipv6/country`
- `ipv6/rir`
- `ipv6/country-rir`
- `asn/country`
- `asn/rir`
- `asn/country-rir`
- `geonames/country`

> See [Data-Format in Common-Header.md](./Common-Header.md#5-data-format)

---

## Glossary

Key terms used throughout the spec (e.g., ASN, RIR, Endianness, etc.)

> See [Glossary.md](./Glossary.md)
