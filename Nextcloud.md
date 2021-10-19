# Nextcloud

## Plugins

*Enable*

[LDAP user and group backend](https://docs.nextcloud.com/server/22/admin_manual/configuration_user/user_auth_ldap.html#)

_**Profile > + APPS > Your apps > LDAP user and group backend > Enable**_

*Install*

_**Profile > + APPS > Organization > Write support for LDAP > Download and enable**_

[Write support for LDAP](https://apps.nextcloud.com/apps/ldap_write_support)


> **Note:** Installation or enabling may require Administrator credentials

> **Note:** App names may differ in other languages

## Setup LDAP

_**Profile > Settings > LDAP/AD integration**_

### LDAP/AD integration

#### Server
| Label | Value | Comment |
|--|--|--|
| Host| `ldap://openldap.ix-openldap.svc.cluster.local` |  |
| User DN | `cn=admin,dc=mydomain,dc=com` |  |
| Password | _`<secret>`_ |  |
| One Base DN per line | `dc=mydomain,dc=com` |  |
| Manually enter LDAP filters (recommended for large directories) | true (checked) |  |

#### Users
| Label | Value | Comment |
|--|--|--|
| Edit LDAP Query | `(objectclass=inetOrgPerson)` |  |

#### Login Attributes
| Label | Value | Comment |
|--|--|--|
| Edit LDAP Query | `(&(objectClass=inetOrgPerson)(\|(uid=%uid)(mail=%uid)))` |  |

#### Groups
| Label | Value | Comment |
|--|--|--|
| Edit LDAP Query | `(objectClass=groupOfNames)` |  |

#### Advanced
| Label | Value | Comment |
|--|--|--|
| **Directory Settings** |
| User Display Name Field | `displayName` |  |
| Base User Tree | `ou=Users,dc=mydomain,dc=com` |  |
| Group Display Name Field | `cn` |  |
| Base Group Tree | `ou=Groups,dc=mydomain,dc=com` |  |
| Group-Member association | `member (AD)` |  |
| **Special Attributes** |
| Quota Field | `` | TBD |
| Quota Default | `` | TBD |
| Email Field | `mail` |  |
| User Home Folder Naming Rule | `` | TBD |
| "$home" Placeholder Fiel | `` | TBD |

#### Writing
| Label | Value | Comment |
|--|--|--|
| Prevent fallback to other backends when creating users or groups. | true (checked) |  |
| To create users, the acting (sub)admin has to be provided by LDAP. | false (unchecked) |  |
| A random user ID has to be generated, i.e. not being provided by the (sub)admin. | false (unchecked) |  |
| An LDAP user must have an email address set. | true (checked) |  |
| Allow users to set their avatar | true (checked) |  |

**User template**
```ldif
dn: cn={UID},{BASE}
objectClass: inetOrgPerson
uid: {UID}
displayName: {UID}
cn: {UID}
sn: {UID}
userPassword: {PWD}
```
