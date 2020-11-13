---
description: >-
  In this document, you can find screens of user interfaces with a description
  of their functionality.
---

# User interfaces of the platform

The main menu \(upper-right corner\) in the guest mode consists of `Login` and `Create Account` functional buttons. By default, the language set to English. To login into the account, a user needs to go to the main menu and click the `Login` button.

![](../.gitbook/assets/image%20%2819%29.png)

The main menu for the authorized user consist of the next elements:

* `Profile` is a button that redirects to a user profile page.
* `Orders` is a button that redirects to a page with user's orders.
* `Wallets` is a button that redirects to a page with user's funds.
* `Trading` is a button that redirects to a trading page.
* `Logout` is a button that ends a session and logout the user from the platform.

In the next chapters, we will look in details on the elements of different pages and describe the functionality of the platform.

![](../.gitbook/assets/menu%20%281%29.jpg)

## 1. Login & Sign up

Authorization window has two tabs: `SIGN IN` and `SIGN UP`. User can switch between login and signup forms clicking the corresponding tab.

**Sign In form description:**

* **Email**: is a field for email. A user needs to enter the email that he used to create an account on the platform. The platform does email validation.
* **Password**: is a field for password. A user needs to enter the password from his account.

On click `SIGN IN` button sends a login request to the platform.

**Forgot your password?** is a text button that brings up a form for a password reset.

![](../.gitbook/assets/image%20%2815%29.png)



If a user has enabled two-factor authentication, the platform brings up a form for 2FA code after a user-entered `Email` and `Password`.

![](../.gitbook/assets/image%20%2813%29.png)

To reset a forgotten password a user needs to perform the next actions:

* Press `Forgot your password?` button. `FORGOT YOUR PASSWORD` window appears.
* In the `FORGOT YOUR PASSWORD` window user needs to enter an email that connected with his account.
* When a user entered the email he needs to click the `Send recovery link on e-mail` button.

After receiving the request to reset the password the platform sends a letter with a reset password link to a user email.

![](../.gitbook/assets/image%20%2816%29.png)

A reset password link that a user receives on his email redirect him to the platform page and brings up the `Create a new password` window. To reset the old password a user needs:

* to enter a new password in the `Password` field.
* to reenter the new password in the `Confirm password` field.
* to click the `SEND` button. If processing was successful, the platform updates the user's password. After that, a user can log in with a new password.

![](../.gitbook/assets/image%20%2812%29.png)

If a user wants to create account he needs to use the `SIGN UP` form. In `SIGN UP` form user needs to enter email, create a password and provide referral code \(optionally\).

**Sign Up form description:**

* **Email**: is a field where user needs to enter his email.
* **Password**: is a field where a user needs to enter a strong password that meets all requirements. Password must be at least 8 characters with one uppercase letter and one number. Entered password goes throw entropy check, also system do dictionary check to prevent the use of common passwords.
* **Confirm password**: is a field where a user needs to enter the same password.
* **Referral Code**: is a field for code from the referral program. Registered users can provide their referral codes for users that are going to registrate on the platform.
* **Terms of Service**: is a Terms of Service checkbox. If a user checked the checkbox it means that he agrees with Terms of Service provided by the platform.

After filling the form, a user needs to click `Sign up` to send a registration request. If the request was successful, the platform creates an account and the user can log in using his credentials.

![](../.gitbook/assets/image%20%2818%29.png)

## 2. Profile

The profile menu consists of three windows: `Security settings`, `My API Keys` and `Account activity`. Account window contains profile information and tools to manage the account.

![](../.gitbook/assets/image%20%2810%29.png)

#### Description of the `Security settings` window: <a id="description-of-the-account-window"></a>

![](../.gitbook/assets/image%20%2811%29.png)

* On the left side of the security settings window, shows an `Email` that belong to a user.
* Under `Email` shows `UID` of a user. `UID` is a unique identifier on a user on the platform.
* The next is a `Password` field with the edit-button on the right side. Clicking the edit button brings up a modal window using. To change a password, a user needs to type an old password in the `Old Password` filed and a new password in `New Password` and `Confirm Password` fields. After that, a user needs to press the `CHANGE` button to apply password changes.

![](../.gitbook/assets/image%20%2814%29.png)

* The `Two-factor authentication` field shows a 2FA status and provide the ability to enable and disable 2FA. When a user clicks the switch button, the platform brings up a form with instructions. A user needs to follow instructions, fill the data and submit the form to enable 2FA.

![](../.gitbook/assets/image%20%2817%29.png)

If a user wants to disable 2FA, he needs to click the 2FA switch button. The platform brings up a window where a user needs to submit 2FA code to disable 2FA.

![2fa disabling](https://www.openware.com/sdk/images/guides/baseapp/2fa_code_disabling.png)

* The `Referral link` is a link that a user can copy and share to affiliate new users to the platform. When an affiliate follows the referral link, the platform opens up the `Sign up` form with pre-filled referral code.
* The `Company verification` is a list of steps that a user needs to pass to get corresponding permissions. By default, a user has to pass several steps to get all permission. 
  * Information about the legal entity is a step with basic information about user's entity. I contains `Legal Business Name`, `Business activity`, `Registration number`, `Country of Registration`, and `E-mail`.

![Information about the legal entity](../.gitbook/assets/image%20%2822%29.png)

*  * Corporate documents. The step where user should upload the corporate documents which are the following: `Document that confirms registration of the company`, `Document that confirms the legal address of the company`, `Document that confirms the authorized person`, `Document that confirms ownership of the company`.

![Corporate documents](../.gitbook/assets/image%20%2823%29.png)

*  * Authorised person details is the next step. This form contains the following fields: `First name`, `Last name`, `Country of residence`, `Day of birth`, `Driving license`, `ID`, `Passport`.

![Authorised person details](../.gitbook/assets/image%20%2824%29.png)

*  * Beneficial owner details is the next step. If beneficial owner and authorised person are the same, user can check this option and the form will fill automatically. However, the fields are the same: `First name`, `Last name`, `Country of residence`, `Day of birth`, `Driving license`, `ID`, `Passport`.

![Beneficial owner details](../.gitbook/assets/image%20%2821%29.png)

*  * If there are any errors, they will be shown in company verification block so user can check them and resubmit the verification. Otherwise, all data will be validated within 24 hours.

![](../.gitbook/assets/image%20%2825%29.png)

#### Description of the `API Token` window: <a id="description-of-the-account-window"></a>

`API Token` is a window for API keys management. To be able to create and manage API keys, a user needs to enable 2FA.

To create a new API key a user needs to click the `Create new` button, then pops up a window for 2FA code in which a user needs to enter 2FA code.

![My API Keys](../.gitbook/assets/image%20%2827%29.png)



![](../.gitbook/assets/image%20%2826%29.png)





