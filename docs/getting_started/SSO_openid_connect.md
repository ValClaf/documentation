# Single Sign-On With OpenID Connect

To make it easier for employees to access SEKOIA.IO, you can enable SSO for users of your SEKOIA.IO community. 

## Prerequisites for OpenID Connect
- Your Identity Provider (IdP) must support the OpenID Connect standard
- Only admin user with the `COMMUNITY_WRITE_ROLE` permission can configure the SSO.

## Configure SSO on SEKOIA.IO

To set up SSO, follow these instructions :

1. Log in to SEKOIA.IO platform
2. Click on your profile picture and select `Account settings` to access the User center
3. Under Manage community > Authicafication, click on the button `Configure`
![SSO_Form](/assets/getting_started/SSO_Authentication.png)

5. Fill in identidy provider details
![SSO_Form](/assets/getting_started/SSO_identity.png)
7. Save the configuration

Once SSO is set up and your IdP is configure to accept requests, users can log in via the Single Sign-on URL available on this page.
Share it with your users.
![SSO_URL](/assets/getting_started/SSO_URL.png)


## “Just-in-time” (JIT) Account Provisioning 
You can choose to enable automatic creation of your users. When your user logs-in for the first time, his/her account will be automatically created. You can set the default role for newly created users. You can choose the default rôle among all the roles available in your community.
![SSO_JIT](/assets/getting_started/SSO_JIT.png)

If you don't enable “just-in-time” account creation, you will have to manually create user accounts. You can find all the details on how to “[Invite users to join your community](https://docs.sekoia.io/getting_started/invite_users/)”.


## Login method
Once you have completed your configuration of OpenID Connect SSO, users will be able to log-in via SSO.
Users who created their account via SSO, can only log in via this method. 
Only users who create their account via invitation and set up username/password can use both methods to log-in: SSO and username/password. 
When the “two-factor authentication” (MFA) is enabled or enforced for your account, you won’t be asked for it when authenticating via your SSO provider.


## Disable Account
To prevent a user from retrieving your organization's data, deactivate the user from your community and your identity provider.



