# Data Section in SIPAICDB Format

The data section of a SIPAICDB file contains the actual records, which represent various types of IP-related or geographical data. These records are arranged in rows, each following a fixed layout defined by the header section.

---

## Structure of Data Section

Each record (row) in the data section is composed of multiple **fields**, with the total number of fields and their types defined by the following headers:

- [`Data-Fields-Count`](./Common-Header.md#data-fields-count)
- [`Data-Field-Name-N`](./Common-Header.md#data-field-name-n)
- [`Data-Field-Type-N`](./Common-Header.md#data-field-type-n)

---

## Field Separator

Each field in a row is separated by a **null byte (`\0`)**, ensuring simple and fast parsing across systems.

---

## Field Data Types

All fields use explicitly defined data types declared in the header section via `Data-Field-Type-N`.

See full list of field types and descriptions in: [Field-Type.md](./Field-Type.md)

Supported types include:

- `u16`
- `u32`
- `u64`
- `f32`
- `char[N]`
- `datetime`
- `date`

---

## Endianness

All **multi-byte integers** (e.g., `u32`, `u64`, `datetime`) are stored in **Big Endian** format.

---

## Record Structure Example

If the format is `ipv4/country`, a record could consist of:

```text
| IP Start Address (u32) | IP Block Count (u32) | Country Code (char[2]) | Allocation Date (date) | Status (char[1]) |
```

Each of these fields will be written in binary, delimited by a `\0` byte.

---

## Example Representation

For a single record:

```text
+----------------+------------------+------------------+------------------+--------------+
| 102.209.228.0  | 1024             | NG               | 20240823         | A            |
+----------------+------------------+------------------+------------------+--------------+
```

The binary record would look like:

```bin
<102.209.228.0 as u32 BE>\0<1024 as u32 BE>\0<'NG'>\0<20240823 as u32>\0<'A'>
```

---

## See Also

- [Common-Header.md](./Common-Header.md) — For defining field names and types  
- [Field-Type.md](./Field-Type.md) — For supported binary data types
