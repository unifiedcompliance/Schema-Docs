# Log In

The public sharing for these wireframes is:

[https://balsamiq.cloud/srj76i4/ptmjb2b](https://balsamiq.cloud/srj76i4/ptmjb2b)

While these are designed here in Balsamiq, we highly suggest that the components be translated into Material-UI React components, found here: [https://react-material-kit.devias.io/authentication/login-unguarded](https://react-material-kit.devias.io/authentication/login-unguarded).

The scope of this portion of the project is to allow known individual to sign in to the system using either an email/password combination or an Auth0 provider.

The layouts expressed in this documentation are for _communication purposes only_. They are not meant to provide branding guidance or even an official look-and-feel. They exist merely to convey the technical aspects of the project. _Real_ designers will create something much more effective.

The sign in screens are presented as modal dialogs and are accessed from the home page.

## Log In

Log In information is a combination of two screens, log in and forgot password.

![Log In dialog](<../../.gitbook/assets/0 (1).png>)

1. We present a link within the sign in dialog to allow the user to _create an account_ if necessary.
2. The user’s sign-in, if manual, is through a _corporate_ e-mail address and associated password.
3. We present a _forgot password_ link for the email/password combination.
4. If the account has this option enabled, the user can sign in through an Auth0 provider.

### Forgot Password

If the user cannot remember their password, they can click a link, provide their email address, and _if that address exists_, can be sent an email to reset their password.

![Password recovery](<../../.gitbook/assets/1 (10).png>)
