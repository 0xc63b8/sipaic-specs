# SIPAIC Specification Glossary

This glossary defines key terms and concepts used throughout the SIPAICDB v1 specification.

---

## ASN (Autonomous System Number)

A unique identifier assigned to a network under a single administrative entity that participates in BGP routing.

---

## Big Endian

A byte order in which the most significant byte is stored first. SIPAICDB uses Big Endian to ensure cross-platform consistency.

---

## CIDR (Classless Inter-Domain Routing)

A method for allocating IP addresses and routing IP packets using variable-length subnet masking.

---

## Data Record

A single structured unit in the data section of the SIPAICDB file, consisting of multiple fields as defined in the header.

---

## Date

A 32-bit integer representing a date in the format `YYYYMMDD`.

---

## Datetime

A 64-bit integer representing a timestamp in seconds since the Unix epoch (`1970-01-01T00:00:00Z`).

---

## Endianness

The order in which bytes are arranged within binary representations of numbers.

---

## Field

A component of a data record representing a single value such as an IP address, country code, ASN, etc.

---

## Field Type

The data type assigned to a field in a record, such as `u32`, `char[2]`, or `date`. See [Field-Type.md](./Field-Type.md).

---

## GeoNames

A geographical database used in SIPAIC for country-level information. Format: `geonames/country`.

---

## Header

Metadata defined at the beginning of the SIPAICDB file that describes the structure and contents of the data section. See [Common-Header.md](./Common-Header.md).

---

## IP Block

A contiguous range of IP addresses, typically represented as a starting address and a block size.

---

## RIB (Routing Information Base)

A table of IP prefixes and routing information collected from BGP updates.

---

## RIR (Regional Internet Registry)

An organization responsible for managing IP address allocations in a given region. Examples: AFRINIC, ARIN, APNIC, LACNIC, RIPE.

---

## SIPAIC

**Simple Internet Protocol Address Information Center** —  A service designed to store, manage, and serve IP address information including allocations, assignments, and related metadata.

---

## SIPAICDB

The binary database format used by SIPAIC to store processed and structured IP-related data. It has a `.sipaicdb` file extension.

---

## Start Line

The first 32 bytes in a SIPAICDB file, containing encoded values like file version, header count, and record count. See [Start-Line.md](./Start-Line.md).

---

## Type/Info Format

The format of the SIPAICDB file content, expressed as a combination of data type and info category, e.g. `ipv4/country`, `asn/rir`. See [Data-Format in Common-Header.md](./Common-Header.md#5-data-format).
