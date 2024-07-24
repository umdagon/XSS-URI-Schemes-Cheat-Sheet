# XSS Attack Examples using Various URI Schemes
**Note: This information is strictly for educational purposes.**

This repository contains examples of Cross-Site Scripting (XSS) attacks using different URI schemes. It demonstrates how attackers can exploit vulnerabilities in web applications by leveraging these schemes to execute malicious scripts.

### Examples

## Example 1: `data` Scheme

The `data` scheme allows embedding data directly in the URI, making it a powerful tool for XSS attacks.

    <a href="data:text/html,<script>alert('XSS')</script>">Click me</a>

This example creates a link that, when clicked, executes JavaScript code showing an alert with the message "XSS".



## Example 2: `javascript` Scheme

The `javascript` scheme allows executing JavaScript code directly from the URI.

    <a href="javascript:alert('XSS')">Click me</a>

Clicking this link executes the JavaScript code `alert('XSS')`.



## Example 3: `vbscript` Scheme

The `vbscript` scheme is used to execute VBScript code in some older versions of Internet Explorer.

    <a href="vbscript:msgbox('XSS')">Click me</a>

This example creates a popup with the message "XSS" using VBScript.



## Example 4: `mailto` Scheme

The `mailto` scheme can be used to create a link that opens an email client but can also contain malicious code.

    <a href="mailto:test@example.com?subject=Hello&body=<script>alert('XSS')</script>">Send Email</a>

Clicking this link opens the email client with the body pre-filled with JavaScript code.



## Example 5: `ftp` Scheme

The `ftp` scheme can be used to create a link pointing to an FTP resource.

    <a href="ftp://example.com/<script>alert('XSS')</script>">Open FTP</a>

This example might be used to perform an XSS attack if the FTP client or browser improperly handles the content.


## Example 6: `tel` Scheme

The `tel` scheme is used to create a link that initiates a phone call and can contain malicious code.

    <a href="tel:1234567890"><script>alert('XSS')</script></a>

In some cases, this might execute JavaScript code when processing the link.



## Example 7: `sms` Scheme

The `sms` scheme can be used to create a link that initiates sending an SMS and can also contain malicious code.

    <a href="sms:+1234567890"><script>alert('XSS')</script></a>

Clicking this link can potentially execute JavaScript code.
##
# XSS Attack Prevention Using Input Validation, Output Encoding, and Content Security Policy

To prevent XSS attacks, it is necessary to apply multiple layers of defense. Here are three main approaches: input validation, output encoding, and using Content Security Policy (CSP).

### 1. Input Validation

**Principles:**
- Use allowlists to define permissible values for each input field. This is more reliable than denylists, which can be circumvented.
- Check the length, format, and range of input data. For example, ensure numerical parameters are within the allowed range, and strings do not exceed length limits.
- For structured data, use regular expressions that cover the entire input string (using `^` and `$` in expressions).

### 2. Output Encoding

**Principles:**
- Apply encoding directly before writing user-controllable data to a page. Use the appropriate encoding method depending on the context (HTML, JavaScript, CSS, URL).
- In HTML context, replace special characters with HTML entities (e.g., `<` becomes `&lt;`, `>` becomes `&gt;`).
- In JavaScript context, use Unicode escaping (e.g., `<` becomes `\u003c`, `>` becomes `\u003e`).
- For HTML attributes, use methods like `setAttribute` or `[attribute]` to avoid JavaScript code injections.

### 3. Content Security Policy (CSP)

**Principles:**
- CSP helps restrict the sources of executable scripts on the page, preventing the execution of malicious scripts even if they are injected into the HTML.
- Use CSP directives to allow script execution only from trusted sources. For example, `script-src 'self' https://trusted.cdn.com` allows scripts only from your domain and the specified CDN.
- Continuously update and test your CSP rules to ensure they cover all potential attack vectors.

### Check this sources to get more detailed information:

1. [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org)
2. [Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/security/cross-site-scripting)
3. [PortSwigger Web Security Academy](https://portswigger.net/web-security/cross-site-scripting/preventing)

These approaches will significantly reduce the risk of XSS attacks in your web applications.


