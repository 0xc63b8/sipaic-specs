# Start Line

The **Start Line** is the first 32 bytes of any SIPAICDB file. It provides essential metadata required to validate and interpret the rest of the file.

---

## Structure

The layout of the 32-byte Start Line is fixed and structured as follows:

| Offset | Length | Field Name        | Description                                      |
|--------|--------|-------------------|--------------------------------------------------|
| 0      | 8      | Magic             | Always `SIPAICDB` (ASCII)                        |
| 8      | 2      | Format Version    | 2-byte unsigned integer, e.g., `0x0100` for v1.0 |
| 10     | 2      | Header Count      | Number of 64-byte headers in the file            |
| 12     | 4      | Data Record Count | Number of records in the data section            |
| 16     | 16     | Reserved          | Reserved for future use (set to `0` for now)     |

All multi-byte integers use **Big Endian** byte order.

---

## Field Details

### Magic

- ASCII string identifying the file format.
- Must be exactly `SIPAICDB`.

### Format Version

- Identifies the SIPAICDB version (major and minor). For version 1.0, the value is `0x01 0x00`.

### Header Count

- Number of headers immediately following the start line. Helps the parser know how the data section records are structured.

### Data Record Count

- Number of fixed-length records in the data section.
- Used to preallocate structures for reading.

### Reserved

- Currently unused.
- Reserved for future compatibility and flags.

---

## Example (Hex Dump)

```hex
53 49 50 41 49 43 44 42 01 00 00 0A 00 00 27 10
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```

- `SIPAICDB` → Magic
- `0100` → Format Version
- `000A` → 10 Headers
- `00002710` → 10000 Records
- `000001F4` → File Size: 500 bytes
- `00000000000000000000000000000000` → Reserved

---

## Related Sections

- [Common-Header.md](./Common-Header.md)
- [Data-Section.md](./Data-Section.md)
