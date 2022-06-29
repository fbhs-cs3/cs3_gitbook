# Email Validity

### Rules for E-mail Address Syntax

[**Source**](https://help.returnpath.com/hc/en-us/articles/220560587-What-are-the-rules-for-email-address-syntax-)

A valid email address has four parts:

* Recipient name
* @ symbol
* Domain name
* Top-level domain

#### Recipient Name

The recipient name may be a maximum of 64 characters long and consist of:

* Uppercase and lowercase letters in English (A-Z, a-z)
* Digits from 0 to 9
* Special characters ! # $ % & ' \* + - / = ? ^ \_ \` { |

A special character cannot appear as the first or last character in an email address or appear consecutively two or more times. The most commonly used special characters are the period (.), underscore(\_), hyphen (-) and plus sign (+).

#### Domain Name

Domain names may be a maximum of 253 characters and consist of:

* Uppercase and lowercase letters in English (A-Z, a-z)
* Digits from 0 to 9
* A hyphen (-)
* A period (.) (used to identify a sub-domain; for example, email.domainsample)

#### Top-level Domain

Top-level domains are the highest level of the domain name system for the Internet and is placed after the domain name in an email address.

Common top-level domains are (but are not limited to):

* .com
* .net
* .org

### Examples

Examples of valid email addresses include:

* `johndoe@domainsample.com`
* `john.doe@domainsample.net`
* `john.doe43@domainsample.co.uk`

Examples of invalid email addresses include:

| Email address           | What makes it invalid                                                                                |
| ----------------------- | ---------------------------------------------------------------------------------------------------- |
| `@domainsample.com`     | The recipient name is missing.                                                                       |
| johndoedomainsample.com | The @ symbol is missing between johndoe and domainsample.com.                                        |
| john.doe@.net           | The domain name (domainsample) is missing after the @ symbol and before the top level domain (.net). |
| john.doe43@domainsample | The top level domain (.co.uk) is missing.                                                            |
