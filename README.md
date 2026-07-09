# CTF Repository

Personal CTF toolkit and writeups.

## Structure

```
.
├── tools/           # Tools, scripts, binaries, wordlists
│   └── ctfkit       # Multi-tool analysis chain (Python)
└── writeups/        # CTF challenge writeups
```

## Tools

| Tool | Description |
|------|-------------|
| `ctfkit` | Multi-tool analysis chain for CTF forensics |

### ctfkit

```bash
./tools/ctfkit image.png                    # full analysis
./tools/ctfkit image.png -f 'LYKN\{[^}]+\}'  # custom flag format
./tools/ctfkit image.png -m strings exif     # specific modules
./tools/ctfkit image.png -i                  # interactive mode
./tools/ctfkit image.png -n                  # skip heavy tools
./tools/ctfkit -l                            # list all modules
```

**Modules (26):** file, strings, exif, hex, image_info, png_chunks, zip, pdf, binwalk, lsb, steghide, outguess, foremost, audio, base64_decode, base, hex_decode, byte_scan, entropy, eof, network, qr, pcap, hash, exif_embedded, lookups

**Dependencies:** `exiftool binwalk foremost steghide outguess zsteg stegolsb tshark imagemagick pngcheck zbarimg`

## Writeups

Each challenge in `writeups/` follows the template.

## License

MIT