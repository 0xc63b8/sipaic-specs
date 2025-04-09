# Field Types in SIPAICDB Format

The SIPAICDB format uses various data field types to represent different kinds of data in the records. These field types define how each field's data is stored and interpreted.

---

## Data Field Types Overview

Each field in a SIPAICDB record is assigned a data type, which indicates how the data is represented in memory and in the binary file. The most common field types used in the SIPAICDB format include number, fixed-length characters, and date types.

---

## List of Field Types

### Number Types

- **`u16` (uint16)**:  
  A 16-bit unsigned integer. Used for smaller numerical values like port numbers or counts.

  **Example Usage**:
  - Port numbers: `u16` is suitable for values between 0 and 65535.
  - Small counters or flags.

- **`u32` (uint32)**:  
  A 32-bit unsigned integer. Typically used to store large numerical values such as IP addresses, ASN numbers, or block counts.

  **Example Usage**:
  - IP address: `u32` can represent an IPv4 address as a 32-bit number.
  - ASN (Autonomous System Number): A 32-bit unsigned integer to identify network systems.

- **`u64` (uint64)**:  
  A 64-bit unsigned integer. Used for large numerical values, especially when representing larger data ranges like large block sizes.

  **Example Usage**:
  - Large counts or ranges that exceed the `u32` range.

- **`f32` (float32)**:  
  A 32-bit precision floating-point number. May be useful but not now.

### Variable Type

- **`char[N]`**:  
  A fixed-length character array of `N` bytes. This is used for fields with a fixed length, such as country codes or region identifiers.

  **Example Usage**:
  - Country code: `"NG"` (fixed length of 2 bytes for "NG").
  - Region identifier: `"AF"`.

### Date/Time Types

- **`datetime`**:  
  A 64-bit integer representing a timestamp in Unix epoch format (seconds since January 1, 1970). This type is used to store precise timestamps.

  **Example Usage**:
  - `1609459200` represents `2021-01-01 00:00:00 UTC`.

- **`date`**:  
  A 32-bit integer representing a date in a simplified format (e.g., YYYYMMDD). This type is used to store dates without time.

  **Example Usage**:
  - `20210101` represents `2021-01-01`.

---

## How Field Types are Used

Each field in a SIPAICDB record is associated with a specific data type. This type defines how the data is serialized into the binary format. For example:

- If a field is of type `u32`, the corresponding data will be encoded as a 4-byte value in the file.
- If a field is of type `char[2]`, it will be encoded as a 2-byte string, and any additional characters will be padded or truncated accordingly.

---

## Endianness

All multi-byte integer field types (`u32`, `u16`, `u64`) are stored in **Big Endian** format. This ensures that the most significant byte is stored first, regardless of the machine architecture, which helps maintain consistency across platforms.

---

## Example: Field Type Usage in SIPAICDB

Consider the following SIPAICDB record for `ipv4-block/country`:

| Field Name       | Field Type | Field Value  |
|------------------|------------|--------------|
| IP Start Address | `u32`      | `1724883200` |
| IP Block Count   | `u32`      | `1024`       |
| Country Code     | `char[2]`  | `NG`         |
| Allocation Date  | `date`     | `20240823`   |

- `IP Start Address` and `IP Block Count` are `u32` types, representing 32-bit unsigned integers.
- `Country Code` is a `char[2]`, representing a fixed-length 2-byte string ("NG").
- `Allocation Date` is a `date`, representing the allocation date as a 32-bit integer (`20240823`).

---

## References

For more details on the specific usage of these field types in SIPAICDB records, refer to the [Common-Header.md](./Common-Header.md) for field names and their associated types.
