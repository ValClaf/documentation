
## Event Categories


The following table lists the data source offered by this integration.

| Data Source | Description                          |
| ----------- | ------------------------------------ |
| `Network device logs` | Firebox can record traffic logs flowing through their firewall. |
| `Network intrusion detection system` | Security logs provided by Firebox include intrusion prevention related records. |





In details, the following table denotes the type of events produced by this integration.

| Name | Values |
| ---- | ------ |
| Kind | `event` |
| Category | `malware`, `network` |
| Type | `info` |




## Event Samples

Find below few samples of events and how they are normalized by SEKOIA.IO.


=== "connection.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000148|sys_name=SystemName\tdevTimeFormat=MMM dd yyyy HH:mm:ss Z\tdevTime=Sep 23 2022 09:51:24 +0200\tpolicy=Any From Firebox-00\tdisp=Allow\tin_if=Firebox\tout_if=LAN\tsrc=10.10.1.1\tsrcPort=46416\tdst=10.10.1.2\tdstPort=443\tip_len=52\tip_TTL=64\tproto=tcp\ttcp_offset=8\ttcp_flag=S\ttcp_seq=4071455733\ttcp_window=4210",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "allowed"
            ],
            "code": "30000148",
            "action": "Allow"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "ingress": {
                "interface": {
                    "name": "Firebox"
                }
            },
            "egress": {
                "interface": {
                    "name": "LAN"
                }
            }
        },
        "rule": {
            "ruleset": "Any From Firebox-00"
        },
        "source": {
            "ip": "10.10.1.1",
            "port": 46416,
            "address": "10.10.1.1"
        },
        "destination": {
            "ip": "10.10.1.2",
            "port": 443,
            "address": "10.10.1.2"
        },
        "network": {
            "transport": "tcp"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "ip": {
                        "len": 52,
                        "ttl": 64
                    },
                    "tcp": {
                        "offset": 8,
                        "flag": "S",
                        "sequence": "4071455733",
                        "window": "4210"
                    }
                }
            }
        },
        "related": {
            "ip": [
                "10.10.1.1",
                "10.10.1.2"
            ]
        }
    }
    	
	```


=== "connection_allow.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000151|serial=000000000000\tpolicy=DNS-srv-00\tdisp=Allow\tin_if=Lab\tout_if=WAN2\tgeo_dst=USA\tsrc=192.168.91.11\tsrcPort=52075\tsrcPostNAT=192.168.0.20\tsrcPostNATPORT=58586\tdst=8.8.4.4\tdstPort=53\tsrc_user=admin@test.org\tduration=38\tsent_bytes=69\trcvd_bytes=185",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "allowed"
            ],
            "code": "30000151",
            "action": "Allow"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "Lab"
                }
            },
            "egress": {
                "interface": {
                    "name": "WAN2"
                }
            }
        },
        "rule": {
            "ruleset": "DNS-srv-00"
        },
        "source": {
            "ip": "192.168.91.11",
            "port": 52075,
            "nat": {
                "ip": "192.168.0.20",
                "port": 58586
            },
            "bytes": 69,
            "address": "192.168.91.11"
        },
        "destination": {
            "ip": "8.8.4.4",
            "port": 53,
            "geo": {
                "country_iso_code": "USA"
            },
            "bytes": 185,
            "address": "8.8.4.4"
        },
        "user": {
            "email": "admin@test.org"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "duration": 38
                }
            }
        },
        "related": {
            "ip": [
                "192.168.0.20",
                "192.168.91.11",
                "8.8.4.4"
            ]
        }
    }
    	
	```


=== "connection_allow2.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000148|serial=000000000000\tpolicy=Any From Firebox-00\tdisp=Allow\tin_if=Firebox\tout_if=Lab\tsrc=192.168.91.253\tsrcPort=35979\tdst=192.168.91.37\tdstPort=24594\tip_len=58\tip_TTL=64\tproto=udp",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "allowed"
            ],
            "code": "30000148",
            "action": "Allow"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "Firebox"
                }
            },
            "egress": {
                "interface": {
                    "name": "Lab"
                }
            }
        },
        "rule": {
            "ruleset": "Any From Firebox-00"
        },
        "source": {
            "ip": "192.168.91.253",
            "port": 35979,
            "address": "192.168.91.253"
        },
        "destination": {
            "ip": "192.168.91.37",
            "port": 24594,
            "address": "192.168.91.37"
        },
        "network": {
            "transport": "udp"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "ip": {
                        "len": 58,
                        "ttl": 64
                    }
                }
            }
        },
        "related": {
            "ip": [
                "192.168.91.253",
                "192.168.91.37"
            ]
        }
    }
    	
	```


=== "connection_allow3.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000151|serial=000000000000\tpolicy=DNS-Wifi-Home-00\tdisp=Allow\tin_if=Wifi_Home\tout_if=Firebox\tgeo_dst=USA\tsrc=10.10.10.11\tsrcPort=38547\tdst=8.8.4.4\tdstPort=53\tdstPostNAT=10.10.10.1\tduration=40\tsent_bytes=60\trcvd_bytes=116",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "allowed"
            ],
            "code": "30000151",
            "action": "Allow"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "Wifi_Home"
                }
            },
            "egress": {
                "interface": {
                    "name": "Firebox"
                }
            }
        },
        "rule": {
            "ruleset": "DNS-Wifi-Home-00"
        },
        "source": {
            "ip": "10.10.10.11",
            "port": 38547,
            "bytes": 60,
            "address": "10.10.10.11"
        },
        "destination": {
            "ip": "8.8.4.4",
            "port": 53,
            "geo": {
                "country_iso_code": "USA"
            },
            "bytes": 116,
            "address": "8.8.4.4"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "duration": 40
                }
            }
        },
        "related": {
            "ip": [
                "10.10.10.11",
                "8.8.4.4"
            ]
        }
    }
    	
	```


=== "connection_deny.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000148|serial=000000000000\tpolicy=Internal Policy\tdisp=Deny\tin_if=WAN1\tout_if=Firebox\tgeo_src=UKR\tsrc=1.2.3.4\tsrcPort=65006\tdst=192.168.1.2\tdstPort=443\tip_len=87\tip_TTL=115\tproto=tcp\ttcp_offset=5\ttcp_flag=A\ttcp_seq=1843525890\ttcp_window=51200\tmsg=tcp syn checking failed (expecting SYN packet for new TCP connection, but received ACK, FIN, or RST instead).",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "denied"
            ],
            "code": "30000148",
            "action": "Deny",
            "reason": "tcp syn checking failed (expecting SYN packet for new TCP connection, but received ACK, FIN, or RST instead)."
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "WAN1"
                }
            },
            "egress": {
                "interface": {
                    "name": "Firebox"
                }
            }
        },
        "rule": {
            "ruleset": "Internal Policy"
        },
        "source": {
            "ip": "1.2.3.4",
            "port": 65006,
            "geo": {
                "country_iso_code": "UKR"
            },
            "address": "1.2.3.4"
        },
        "destination": {
            "ip": "192.168.1.2",
            "port": 443,
            "address": "192.168.1.2"
        },
        "network": {
            "transport": "tcp"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "ip": {
                        "len": 87,
                        "ttl": 115
                    },
                    "tcp": {
                        "offset": 5,
                        "flag": "A",
                        "sequence": "1843525890",
                        "window": "51200"
                    }
                }
            }
        },
        "related": {
            "ip": [
                "1.2.3.4",
                "192.168.1.2"
            ]
        }
    }
    	
	```


=== "dhcp_pack.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|16000065|serial=000000000000\tmsg=DHCPACK on 10.0.2.52 to 00:01:21:30:0f:a0 (Lab001) via vlan2",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "info"
            ],
            "code": "16000065",
            "reason": "DHCPACK on 10.0.2.52 to 00:01:21:30:0f:a0 (Lab001) via vlan2"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000"
        },
        "source": {
            "ip": "10.0.2.52",
            "mac": "00:01:21:30:0f:a0",
            "domain": "Lab001",
            "address": "Lab001"
        },
        "watchguard": {
            "firebox": {
                "dhcp": {
                    "operation": "ack"
                }
            }
        },
        "related": {
            "hosts": [
                "Lab001"
            ],
            "ip": [
                "10.0.2.52"
            ]
        }
    }
    	
	```


=== "dhcp_request.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|16000066|serial=000000000000\tmsg=DHCPREQUEST for 10.0.2.52 from 00:01:21:30:0f:a0 (Lab001) via vlan2",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "info"
            ],
            "code": "16000066",
            "reason": "DHCPREQUEST for 10.0.2.52 from 00:01:21:30:0f:a0 (Lab001) via vlan2"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000"
        },
        "source": {
            "ip": "10.0.2.52",
            "mac": "00:01:21:30:0f:a0",
            "domain": "Lab001",
            "address": "Lab001"
        },
        "watchguard": {
            "firebox": {
                "dhcp": {
                    "operation": "request"
                }
            }
        },
        "related": {
            "hosts": [
                "Lab001"
            ],
            "ip": [
                "10.0.2.52"
            ]
        }
    }
    	
	```


=== "dpi_http_1.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|1AFF0024|serial=000000000000\tpolicy=HTTPS-LAN-00\tdisp=Allow\tin_if=LAN\tout_if=WAN2\tgeo_dst=USA\tsrc=10.10.1.22\tsrcPort=52804\tdst=5.6.7.8\tdstPort=443\tproto=tcp\tproxy_act=HTTP-Client-LAN\top=GET\tdstname=www.forbidden.com\targ=/favicon.ico\tsent_bytes=604\trcvd_bytes=0\telapsed_time=0.001407 sec(s)\tapp_id=173\tapp_cat_id=5\tapp_name=Forbidden.com\tapp_cat_name=Media streaming services\tsig_vers=18.230\treputation=-1\tmsg=HTTP request",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "allowed"
            ],
            "code": "1AFF0024",
            "action": "Allow",
            "reason": "HTTP request"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "LAN"
                }
            },
            "egress": {
                "interface": {
                    "name": "WAN2"
                }
            }
        },
        "rule": {
            "category": "HTTP-Client-LAN",
            "ruleset": "HTTPS-LAN-00"
        },
        "source": {
            "ip": "10.10.1.22",
            "port": 52804,
            "bytes": 604,
            "address": "10.10.1.22"
        },
        "destination": {
            "ip": "5.6.7.8",
            "domain": "www.forbidden.com",
            "port": 443,
            "geo": {
                "country_iso_code": "USA"
            },
            "bytes": 0,
            "address": "www.forbidden.com",
            "top_level_domain": "com",
            "subdomain": "www",
            "registered_domain": "forbidden.com"
        },
        "network": {
            "transport": "tcp"
        },
        "http": {
            "request": {
                "method": "GET"
            }
        },
        "url": {
            "path": "/favicon.ico",
            "domain": "www.forbidden.com",
            "top_level_domain": "com",
            "subdomain": "www",
            "registered_domain": "forbidden.com"
        },
        "watchguard": {
            "firebox": {
                "application": {
                    "id": 173,
                    "name": "Forbidden.com",
                    "category": {
                        "id": 5,
                        "name": "Media streaming services"
                    },
                    "reputation": -1
                }
            }
        },
        "related": {
            "hosts": [
                "www.forbidden.com"
            ],
            "ip": [
                "10.10.1.22",
                "5.6.7.8"
            ]
        }
    }
    	
	```


=== "dpi_http_2.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|2CFF0009|serial=000000000000\tpolicy=HTTPS-LAN-00\tdisp=Allow\tin_if=LAN\tout_if=WAN2\tgeo_dst=USA\tsrc=10.10.1.22\tsrcPort=52803\tdst=5.6.7.8\tdstPort=443\tproto=tcp\tproxy_act=HTTPS-Client-LAN\ttls_profile=TLS-Client-HTTPS\tinspect_action=HTTP-Client-LAN\tserver_ssl=TLS_AES_128_GCM_SHA256\tclient_ssl=TLS_AES_128_GCM_SHA256\ttls_version=TLS_V13\tmsg=ProxyInspect: HTTPS content inspection",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "allowed"
            ],
            "code": "2CFF0009",
            "action": "Allow",
            "reason": "ProxyInspect: HTTPS content inspection"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "LAN"
                }
            },
            "egress": {
                "interface": {
                    "name": "WAN2"
                }
            }
        },
        "rule": {
            "category": "HTTPS-Client-LAN",
            "ruleset": "HTTPS-LAN-00"
        },
        "source": {
            "ip": "10.10.1.22",
            "port": 52803,
            "address": "10.10.1.22"
        },
        "destination": {
            "ip": "5.6.7.8",
            "port": 443,
            "geo": {
                "country_iso_code": "USA"
            },
            "address": "5.6.7.8"
        },
        "network": {
            "transport": "tcp"
        },
        "tls": {
            "cipher": "TLS_AES_128_GCM_SHA256",
            "version": "TLS_V13"
        },
        "watchguard": {
            "firebox": {
                "tls": {
                    "profile": "TLS-Client-HTTPS"
                }
            }
        },
        "related": {
            "ip": [
                "10.10.1.22",
                "5.6.7.8"
            ]
        }
    }
    	
	```


=== "dpi_http_deny.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|1AFF0021|serial=000000000000\tpolicy=HTTPS-LAN-00\tdisp=Deny\tin_if=LAN\tout_if=WAN2\tgeo_dst=USA\tsrc=10.10.1.22\tsrcPort=52803\tdst=5.6.7.8\tdstPort=443\tproto=tcp\tproxy_act=HTTP-Client-LAN\tcats=Sex\top=GET\tdstname=www.forbidden.com\targ=/\taction=www.forbidden.com\tmsg=ProxyDeny: HTTP Request categories",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "denied"
            ],
            "code": "1AFF0021",
            "action": "Deny",
            "reason": "ProxyDeny: HTTP Request categories"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "LAN"
                }
            },
            "egress": {
                "interface": {
                    "name": "WAN2"
                }
            }
        },
        "rule": {
            "category": "HTTP-Client-LAN",
            "ruleset": "HTTPS-LAN-00"
        },
        "source": {
            "ip": "10.10.1.22",
            "port": 52803,
            "address": "10.10.1.22"
        },
        "destination": {
            "ip": "5.6.7.8",
            "domain": "www.forbidden.com",
            "port": 443,
            "geo": {
                "country_iso_code": "USA"
            },
            "address": "www.forbidden.com",
            "top_level_domain": "com",
            "subdomain": "www",
            "registered_domain": "forbidden.com"
        },
        "network": {
            "transport": "tcp"
        },
        "http": {
            "request": {
                "method": "GET"
            }
        },
        "url": {
            "path": "/",
            "domain": "www.forbidden.com",
            "top_level_domain": "com",
            "subdomain": "www",
            "registered_domain": "forbidden.com"
        },
        "related": {
            "hosts": [
                "www.forbidden.com"
            ],
            "ip": [
                "10.10.1.22",
                "5.6.7.8"
            ]
        }
    }
    	
	```


=== "game_allow.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000149|serial=000000000000\tpolicy=HTTPS-Wifi-Home-00\tdisp=Allow\tin_if=Wifi_Home\tout_if=WAN2\tgeo_dst=GBR\tsrc=10.10.10.7\tsrcPort=61561\tsrcPostNAT=192.168.0.20\tdst=104.98.231.118\tdstPort=443\tip_len=364\tip_TTL=64\tproto=tcp\ttcp_offset=5\ttcp_flag=A\ttcp_seq=2533718466\ttcp_window=258\tapp=Sony PlayStation\tapp_cat=Online games\tapp_behavior=Access\tmsg=Application identified",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "allowed"
            ],
            "code": "30000149",
            "action": "Allow",
            "reason": "Application identified"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "Wifi_Home"
                }
            },
            "egress": {
                "interface": {
                    "name": "WAN2"
                }
            }
        },
        "rule": {
            "ruleset": "HTTPS-Wifi-Home-00"
        },
        "source": {
            "ip": "10.10.10.7",
            "port": 61561,
            "nat": {
                "ip": "192.168.0.20"
            },
            "address": "10.10.10.7"
        },
        "destination": {
            "ip": "104.98.231.118",
            "port": 443,
            "geo": {
                "country_iso_code": "GBR"
            },
            "address": "104.98.231.118"
        },
        "network": {
            "transport": "tcp",
            "application": "Sony PlayStation"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "ip": {
                        "len": 364,
                        "ttl": 64
                    },
                    "tcp": {
                        "offset": 5,
                        "flag": "A",
                        "sequence": "2533718466",
                        "window": "258"
                    }
                },
                "application": {
                    "name": "Sony PlayStation",
                    "category": {
                        "name": "Online games"
                    },
                    "behavior": "Access"
                }
            }
        },
        "related": {
            "ip": [
                "10.10.10.7",
                "104.98.231.118",
                "192.168.0.20"
            ]
        }
    }
    	
	```


=== "geo_deny.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000173|serial=000000000000\tpolicy=WatchGuard SSLVPN-00\tdisp=Deny\tin_if=WAN1\tout_if=Firebox\tgeo_src=UKR\tgeo=geo_src\tsrc=1.2.3.4\tsrcPort=65006\tdst=192.168.1.2\tdstPort=443\tip_len=52\tip_TTL=115\tproto=tcp\ttcp_offset=8\ttcp_flag=S\ttcp_seq=1826748674\ttcp_window=51200\tmsg=blocked sites (geolocation source)",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "denied"
            ],
            "code": "30000173",
            "action": "Deny",
            "reason": "blocked sites (geolocation source)"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "WAN1"
                }
            },
            "egress": {
                "interface": {
                    "name": "Firebox"
                }
            }
        },
        "rule": {
            "ruleset": "WatchGuard SSLVPN-00"
        },
        "source": {
            "ip": "1.2.3.4",
            "port": 65006,
            "geo": {
                "country_iso_code": "UKR"
            },
            "address": "1.2.3.4"
        },
        "destination": {
            "ip": "192.168.1.2",
            "port": 443,
            "address": "192.168.1.2"
        },
        "network": {
            "transport": "tcp"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "ip": {
                        "len": 52,
                        "ttl": 115
                    },
                    "tcp": {
                        "offset": 8,
                        "flag": "S",
                        "sequence": "1826748674",
                        "window": "51200"
                    }
                }
            }
        },
        "related": {
            "ip": [
                "1.2.3.4",
                "192.168.1.2"
            ]
        }
    }
    	
	```


=== "no_rule_deny.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|30000148|serial=000000000000\tpolicy=Unhandled External Packet-00\tdisp=Deny\tin_if=WAN1\tout_if=Firebox\tgeo_src=CHN\tsrc=1.2.3.4\tsrcPort=35186\tdst=192.168.1.2\tdstPort=6379\tip_len=60\tip_TTL=49\tproto=tcp\ttcp_offset=10\ttcp_flag=S\ttcp_seq=2630166840\ttcp_window=4210",
        "event": {
            "kind": "event",
            "category": [
                "network"
            ],
            "type": [
                "connection",
                "denied"
            ],
            "code": "30000148",
            "action": "Deny"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "WAN1"
                }
            },
            "egress": {
                "interface": {
                    "name": "Firebox"
                }
            }
        },
        "rule": {
            "ruleset": "Unhandled External Packet-00"
        },
        "source": {
            "ip": "1.2.3.4",
            "port": 35186,
            "geo": {
                "country_iso_code": "CHN"
            },
            "address": "1.2.3.4"
        },
        "destination": {
            "ip": "192.168.1.2",
            "port": 6379,
            "address": "192.168.1.2"
        },
        "network": {
            "transport": "tcp"
        },
        "watchguard": {
            "firebox": {
                "network": {
                    "ip": {
                        "len": 60,
                        "ttl": 49
                    },
                    "tcp": {
                        "offset": 10,
                        "flag": "S",
                        "sequence": "2630166840",
                        "window": "4210"
                    }
                }
            }
        },
        "related": {
            "ip": [
                "1.2.3.4",
                "192.168.1.2"
            ]
        }
    }
    	
	```


=== "virus_analysis.json"

    ```json
	
    {
        "message": "LEEF:1.0|WatchGuard|XTM|12.8.2.B666661|1AFF0018|serial=000000000000\tpolicy=HTTP-Wifi-WGCloud-00\tdisp=Allow\tin_if=Mgmt\tout_if=WAN2\tgeo_dst=USA\tsrc=10.0.2.54\tsrcPort=49946\tdst=5.6.7.8\tdstPort=80\tproto=tcp\tproxy_act=HTTP-Wifi-WGCloud\trule_name=All text types\tcontent_type=text/html\tmsg=ProxyAvScan: HTTP Content Type match",
        "event": {
            "kind": "event",
            "category": [
                "malware"
            ],
            "type": [
                "info"
            ],
            "code": "1AFF0018",
            "action": "Allow",
            "reason": "ProxyAvScan: HTTP Content Type match"
        },
        "observer": {
            "type": "firewall",
            "product": "XTM",
            "vendor": "WatchGuard",
            "version": "12.8.2.B666661",
            "serial_number": "000000000000",
            "ingress": {
                "interface": {
                    "name": "Mgmt"
                }
            },
            "egress": {
                "interface": {
                    "name": "WAN2"
                }
            }
        },
        "rule": {
            "category": "HTTP-Wifi-WGCloud",
            "ruleset": "HTTP-Wifi-WGCloud-00",
            "name": "All text types"
        },
        "source": {
            "ip": "10.0.2.54",
            "port": 49946,
            "address": "10.0.2.54"
        },
        "destination": {
            "ip": "5.6.7.8",
            "port": 80,
            "geo": {
                "country_iso_code": "USA"
            },
            "address": "5.6.7.8"
        },
        "network": {
            "transport": "tcp"
        },
        "http": {
            "response": {
                "mime_type": "text/html"
            }
        },
        "related": {
            "ip": [
                "10.0.2.54",
                "5.6.7.8"
            ]
        }
    }
    	
	```





## Extracted Fields

The following table lists the fields that are extracted, normalized under the ECS format, analyzed and indexed by the parser. It should be noted that infered fields are not listed.

| Name | Type | Description                |
| ---- | ---- | ---------------------------|
|`destination.bytes` | `long` | Bytes sent from the destination to the source. |
|`destination.domain` | `keyword` | The domain name of the destination. |
|`destination.geo.country_iso_code` | `keyword` | Country ISO code. |
|`destination.ip` | `ip` | IP address of the destination. |
|`destination.nat.ip` | `ip` | Destination NAT ip |
|`destination.nat.port` | `long` | Destination NAT Port |
|`destination.port` | `long` | Port of the destination. |
|`event.action` | `keyword` | The action captured by the event. |
|`event.category` | `keyword` | Event category. The second categorization field in the hierarchy. |
|`event.code` | `keyword` | Identification code for this event. |
|`event.kind` | `keyword` | The kind of the event. The highest categorization field in the hierarchy. |
|`event.reason` | `keyword` | Reason why this event happened, according to the source |
|`event.type` | `keyword` | Event type. The third categorization field in the hierarchy. |
|`http.request.method` | `keyword` | HTTP request method. |
|`http.response.mime_type` | `keyword` | Mime type of the body of the response. |
|`network.application` | `keyword` | Application level protocol name. |
|`network.transport` | `keyword` | Protocol Name corresponding to the field `iana_number`. |
|`observer.egress.interface.name` | `keyword` | Interface name |
|`observer.ingress.interface.name` | `keyword` | Interface name |
|`observer.product` | `keyword` | The product name of the observer. |
|`observer.serial_number` | `keyword` | Observer serial number. |
|`observer.type` | `keyword` | The type of the observer the data is coming from. |
|`observer.vendor` | `keyword` | Vendor name of the observer. |
|`observer.version` | `keyword` | Observer version. |
|`rule.category` | `keyword` | Rule category |
|`rule.name` | `keyword` | Rule name |
|`rule.ruleset` | `keyword` | Rule ruleset |
|`source.bytes` | `long` | Bytes sent from the source to the destination. |
|`source.domain` | `keyword` | The domain name of the source. |
|`source.geo.country_iso_code` | `keyword` | Country ISO code. |
|`source.ip` | `ip` | IP address of the source. |
|`source.mac` | `keyword` | MAC address of the source. |
|`source.nat.ip` | `ip` | Source NAT ip |
|`source.nat.port` | `long` | Source NAT port |
|`source.port` | `long` | Port of the source. |
|`tls.cipher` | `keyword` | String indicating the cipher used during the current connection. |
|`tls.version` | `keyword` | Numeric part of the version parsed from the original string. |
|`url.domain` | `keyword` | Domain of the url. |
|`url.path` | `wildcard` | Path of the request, such as "/search". |
|`user.email` | `keyword` | User email address. |
|`watchguard.firebox.application.behavior` | `keyword` | The action done by the application |
|`watchguard.firebox.application.category.id` | `number` | The identifier of the category the application is related to |
|`watchguard.firebox.application.category.name` | `keyword` | The name of the category the application is related to |
|`watchguard.firebox.application.duration` | `number` | The number of seconds the connectio lasted |
|`watchguard.firebox.application.id` | `number` | The internal identifier of the application |
|`watchguard.firebox.application.name` | `keyword` | The name of the application |
|`watchguard.firebox.application.reputation` | `number` | The reputation of the application |
|`watchguard.firebox.dhcp.operation` | `keyword` | The DHCP Operation |
|`watchguard.firebox.network.duration` | `number` | The number of seconds the connection lasted |
|`watchguard.firebox.network.ip.len` | `number` | The length of the entire IP packet, including both the header and data segments, in bytes |
|`watchguard.firebox.network.ip.ttl` | `number` | The number of hops the IP packet can still travel before being considered as expired |
|`watchguard.firebox.network.tcp.flag` | `keyword` | The control flag of the data flow |
|`watchguard.firebox.network.tcp.offset` | `number` | The size of the tcp header |
|`watchguard.firebox.network.tcp.sequence` | `keyword` | The sequence number of the tcp connection |
|`watchguard.firebox.network.tcp.window` | `keyword` | The size of the sliding window |
|`watchguard.firebox.tls.profile` | `keyword` | The TLS profile |

