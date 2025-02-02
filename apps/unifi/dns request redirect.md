https://gist.github.com/terafin/2ee5b231cb36712b0d2b7dd32941c2ab

Group ID:

61830f852c540a04b0c4f7ac

cloud key

```json
{
        "service": {
                "nat": {
                        "rule": {
                                "10": {
                                        "description": "transparent dns redirection",
                                        "destination": {
                                                "group": {
                                                        "address-group": "!61830f852c540a04b0c4f7ac"
                                                },
                                                "port": "53"
                                        },
                                        "inbound-interface": "eth1.8",
                                        "inside-address": {
                                                "address": "10.36.10.20"
                                        },
                                        "log": "enable",
                                        "protocol": "tcp_udp",
                                        "type": "destination"
                                }
                        }
                }
        }
}
```

