# openwrt-21.02.2

#caddy-v1 binary(with webdav)

#Caddyfile example:
0.0.0.0:8080
{
gzip
basicauth / admin password
webdav /webdav {
scope /mnt
}
root /mnt
browse
}

#caddy-v2 binary(with webdav)

#Caddyfile example:
:8080
{
encode gzip
basicauth {
admin JDJhJDEwJFRKOUM1eVZKbkg4LzA0OWMvRElsbi5sSmx1TFpXcExaNmV2ajRFUGkvSUkuYTY5S05JOUlt
}
root * /mnt/sda1

route {
	rewrite /webdav /webdav/
	webdav /webdav/* {
		prefix /webdav
	}
	file_server browse
}
}
