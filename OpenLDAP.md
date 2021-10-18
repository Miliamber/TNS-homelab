# OpenLDAP

| Label | Value | Comment |
|--|--|--|
| Application Name * | `openldap` | name is important for DNS link[^1] |
| LDAP_ORGANISATION * | `mylab` | only informational |
| LDAP_DOMAIN * | `mydomain.com` |  |
| LDAP_ADMIN_PASSWORD * | _`<secret>`_ | secure password |
| LDAP_CONFIG_PASSWORD * | _`<secret>`_ | secure password |
| LDAP_BASE_DN * | `DC=mydomain,DC=com` | proposal for your domain but can be anything else |

## Base

```ldif
#   base dn
dn: dc=mydomain,dc=com
objectClass: top
objectClass: dcObject
objectClass: organization
o: mylab
dc: 278
 
#   OU for all user objects [used in: Athelia, Nextcloud]
dn: ou=Users,dc=mydomain,dc=com
objectClass: top
objectClass: organizationalUnit
ou: Users
 
#   OU for all group objects [used in: Athelia, Nextcloud]
dn: ou=Groups,dc=mydomain,dc=com
objectClass: top
objectClass: organizationalUnit
ou: Groups
 
#   OU for devices (e.g. Computer,Mobiles) [used in: freeradius]
dn: ou=Devices,dc=mydomain,dc=com
objectClass: top
objectClass: organizationalUnit
ou: Devices
```

## User
```ldif
dn: cn=MyUser,ou=Users,dc=mydomain,dc=com
displayName: My User
mail: myuser@mydomain.com
uid: myuser
cn: myuser
objectClass: inetOrgPerson
sn: user
userPassword: {sha}g0DpQLeDmOWAvkaIUfDFLuhxyk0=
```

## Group
```ldif
dn: cn=mygroupname,ou=Groups,dc=mydomain,dc=com
objectClass: groupOfNames
objectClass: top
cn: mygroupname
```
## Device



[^1]: internal dns names: https://truecharts.org/manual/Quick-Start%20Guides/14-linking-apps/