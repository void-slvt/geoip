# GeoIP для xray с добавленными заблокированными автономными системами (ASN)
В этом репозитории каждый день генерируются геофайлы со стандартными кодами стран из db-ip, а так же дополнительными категориями заблокированных РКН ASN:

```jsonc
"routing": {
    "rules": [
        {
            "outboundTag": "direct",
            "ip": [
                "geoip:ru"            // Все ip-адреса принадлежащие РУ региону
            ]
        },
        {
            "outboundTag": "proxy",
            "ip": [
                "geoip:oracle",       // AS31898, AS54253, AS1219, AS6142, AS14544, AS20054
                "geoip:akamai",       // AS20940, AS16625, AS12222, AS33905, AS63949
                "geoip:hetzner",      // AS24940, AS213230, AS212317, AS215859
                "geoip:scaleway",     // AS12876, AS29447
                "geoip:digitalocean", // AS14061, AS46652
                "geoip:aws",          // AS16509, AS14618, AS8987
                "geoip:cdn77",        // AS60068, AS212238
                "geoip:cloudflare",   // AS13335
                "geoip:fastly",       // AS54113
                "geoip:ovh",          // AS16276
                "geoip:vultr",        // AS20473
                "geoip:creanova",     // AS51765
                "geoip:telegram"      // AS62041
                "geoip:banned_asn"    // Все вышеперечисленные ASN в одном теге
            ]
        },
    ]
}
```

# Ссылки для загрузки:

Последняя версия `geoip.dat`:
https://github.com/void-slvt/geoip/releases/latest/download/geoip.dat

# Источник данных

CIDR подсети берутся утилитой `bgpq4` для каждой ASN. На данный момент используются только IPv4 адреса для снижения размера геофайлов ввиду малой распространенности IPv6 в РФ.
