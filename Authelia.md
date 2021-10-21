# Authelia

| Label | Value | Comment |
|--|--|--|
| Application Name * | `authelia` | name is important for DNS link[^1] |
| Domain * | `mydomain.com` | |
| Default Redirection Url | `https://sso.mydomain.com` | If user tries to authenticate without any referer, this is used |
| Issuer | _`<MyDomain>`_ | The issuer name displayed in the Authenticator application of your choice |
| LDAP backend configuration | true (checked) | We will use LDAP for users and groups |
| URL * | `ldap://openldap.ix-openldap.svc.cluster.local` | internal dns name, please see[^1] |
| Base DN * | `DC=mydomain,DC=com` | base of openldap |
| Username Attribute *| `uid` | e.g. cn or any similar attribute can be used |
| Users Filter * | `(&({username_attribute}={input})(objectClass=inetOrgPerson))` | identification of an user |
| Additional Groups DN * | `OU=Groups` |  |
| Groups Filter * | `(&(member={dn})(objectClass=groupOfNames))` | identification of an group |
| Group name Attribute * | `cn` |  |
| Mail Attribute * | `mail` |  |
| Display Name Attribute | `displayName` |  |
| Admin User * | `CN=admin,DC=mydomain,DC=com` | TODO: check if readonly is also working |
| Password * | _`<secret>`_ |  |
| SMTP Provider | true (checked) | please enter in the following fields your SMTP settings |
| Enable Ingress | true (checked) | please enter your SSL settings |

## Optional settings
| Label | Value | Comment |
|--|--|--|
| Theme | `dark` | color schema |



[^1]: internal dns names: https://truecharts.org/manual/Quick-Start%20Guides/14-linking-apps/