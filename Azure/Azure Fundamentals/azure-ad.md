# Identity, Authentication, Authorization and Azure AD

Azure AD is a cloud identity provider. Azure Active Directory is now Microsoft Entra ID.

Entra ID supports following protocols for authentication:
- OpenID
- SAML
- WS-Fed
- OAuth2

There are many ways you can authenticate:
1. Something I know(password, PIN).
2. Something I have(token, phone).
3. Something I am(biometric).

Multifactor authentication combines multiple ways of authenticating. It is available
in Entra ID when using security defaults.

Authorization is about what the users can do.

Conditional is access is acting as a gateway anytime you ask Azure for a token. 
With certain conditions you can have requirements, for example you can require MFA or trusted device to be used.

Tenants can be used by Azure, Microsoft 365 and third party applications.

Using Connect, you can synchronize on premise Active Directory with the one on the cloud.