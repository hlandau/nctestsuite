Test Suite Format
-----------------

A test suite file is a series of entries.

Each entry consists of a series of lines:

    Entry:
      One or more of:
        "IN"    [test-id]
        name              (e.g. "d/example")
        value             (in JSON form, on one line)

      "OUT" [num-errors]
      Zero or more DNS records in zone-file format
      All names used must be fully qualified with trailing dots.
      All names used must be in lowercase.
      Fields should be separated by single spaces.
      Hexadecimal fields should be encoded in uppercase.
      Each record line may be prefixed by a tag followed by a space.
      The following tags are allowed:

        - `AN`: For DNS query-based validation, the record must be in the Answer section.
        - `NS`: For DNS query-based validation, the record must be in the Authority section.
        - `AR`: For DNS query-based validation, the record must be in the Additional section.

      Implementations should ignore tags they do not understand.
      Tags will always begin with an uppercase character at the start of a line and be terminated
      by a space.

      The first IN line of an entry may optionally contain a test ID to identify the test.
      The OUT line may optionally contain an error count which indicates the number of parse errors.
      If omitted, it is taken to be zero.

Blank lines and lines starting with # are ignored.

The multiple IN blocks which are allowed enable the specification of multiple
Namecoin key-value pairs for the purposes of testing import and delegation
features.
