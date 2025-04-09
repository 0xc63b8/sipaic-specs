# Common Headers in SIPAICDB

This document defines and explains the common headers used in SIPAICDB binary files. These headers are placed immediately after the **Start Line** and provide metadata that guides how the file is interpreted.

---

## Common Headers

### 1. `Checksum`

An optional checksum value for the file or data segment integrity validation.

### 2. `Data-Fields-Count`

Number of fields in each data record.

### 3. `Data-Field-Name-N`

The name of the N-th field in the data section. Example: `Data-Field-Name-1:ip_start`

### 4. `Data-Field-Type-N`

The type of the N-th field. Types are defined in [Field-Type.md](./Field-Type.md).

### 5. `Data-Format`

Indicates the type of data stored in the file and its content scope.

**Format:** `type/data-info`

#### Supported Types and Data-Info

- `ipv4/country`: Map IPv4 Block to country ISO Alpha-2 code.
- `ipv4/rir`: Map IPv4 Block to RIR info that allocate the IP block.
- `ipv4/country-rir` Map IPv4 Block to both country ISO code and RIR info.
- `ipv6/country`: Like `ipv4/country` but for IPv6 Block.
- `ipv6/rir`: Like `ipv4/rir` but for IPv6 Block.
- `ipv6/country-rir`: Like `ipv4/country-rir` but for IPv6 Block.
- `geospatial/country`: ISO Alpha-2 mapped to country metadata (name, continent, etc.)
- `asn/country`: Map ASN to country ISO Alpha-2 code.
- `asn/rir`: Map ASN to RIR info that allocate the IP block.
- `asn/country-rir`: Map ASN to both country ISO code and RIR info.

**See also:** [Field Types](./Field-Type.md) and [Data Section](./Data-Section.md)

### 6. `Data-Record-Length`

Length in bytes of each record in the data section.

### 7. `Generated-By`

The name or identifier of the software/system that generated the file, e.g., `SIPAIC Generator`.

### 8. `Generated-Date`

The Unix epoch timestamp when the file was generated. Example: `1700000000`.

### 9. `Generated-Since`

The epoch timestamp marking the start time of the generator session that produced this file.

### 10. `Generated-Version`

Version of the software used to generate the file, e.g., `v1.2`, only support major and minor.

### 11. `Generated-Version-Number`

Internal version number of the generator format. Example: `100` for v1.0.

---

## Required Headers

These headers are **required** in every SIPAICDB file:

- `Checksum`
- `Data-Format`
- `Data-Record-Length`
- `Data-Fields-Count`
- `Data-Field-Name-N`
- `Data-Field-Type-N`

---

## Example Headers

```txt
Data-Format:ipv4/country
Generated-By:SIPAIC Generator
Generated-Version:v1.2
Generated-Version-Number:102
Generated-Date:1700000000
Generated-Since:1699990000
Data-Record-Length:14
Data-Fields-Count:4
Data-Field-Name-1:ip_start
Data-Field-Type-1:u32
Data-Field-Name-2:ip_count
Data-Field-Type-2:u32
Data-Field-Name-3:country
Data-Field-Type-3:char[2]
Data-Field-Name-4:allocated_date
Data-Field-Type-4:date
```

---

For more details about how the data fields are stored and interpreted, see the [Data Section](./Data-Section.md).
