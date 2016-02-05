sar

Usage: sar -f <argument> <other sar args>

This is a wrapper for "sar". It magically hanles the "-f" option. All
other options are passed verbatim to sar. If the argument to the "-f"
option:

    *   exists and can be opened, then treat as-is.

    *   is a number, then we assume it's the day-of-the-month and we simply
        prepend /var/lib/sa/sa.

    *   (possibly after previous step) does not exist, try to decompress.
        The decompressed file is saved as a tempfile (see mktemp). It is
        removed when the program completes.

Decompression tries first gzip, then xz, then bzip2.

