---
tags:
    - network
    - tracing
    - tshark
---

# TShark
## Capture specific packets with capture filter on any interface
```bash
tshark -f "host 192.168.1.1" -i any
```

## Capture everything on any interface and use display filter
```bash
tshark -Y "icmp" -i any
```