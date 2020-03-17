# UiPathTeam.WindowsCredentialManager.Activities

This is a UiPath Library component aimed at exposing simple activities to manage credentials stored in the Windows Credential Manager.

Developed with UiPath Studio 19.10.4

It is a wrapper on top of the [CredentialManager](https://www.nuget.org/packages/CredentialManagement) package.

Source code available on [github](https://github.com/ilyalozovyy/credentialmanagement).

A note about Security:

This pakage relies on SecureString for password variable and the Windows Credential Manager.

Both these mechanisms are know to be very limited in terms of Security:

* a SecureString can be converted into a String in 1 line of standard .Net code
* the Windows Credential Manager allows access from any user process to any of the credentials of that user

Please keep the above in mind when adopting this component.
The advantages of using the Windows Credential Manager include:

* a standard practice (albeit aging one) for credential storage in Windows (e.g. better than included in config file)
* offers flexibility because dynamic (e.g. remember credentials in the scope of attended automation)

Extra remark:

`Get Windows Credential` of an inexistent `Target` will result in a PersistenceType value of 0.

For .Net enthusiats, this means the standard way of of testing for the return value being undefined looks like the following:

```[Enum].IsDefined(GetType(CredentialManagement.PersistanceType), persistenceType)```
where `persistenceType` is the variable to check.

### LICENSE
[UiPath Open Platform License Agreement](https://www.uipath.com/hubfs/legalspot/UiPath_Activity_License_Agreement.pdf)