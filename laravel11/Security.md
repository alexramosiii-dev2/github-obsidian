### CSRF (Cross-Site Request Forgery)
How does it happen:
-  if you logged in to domain1, your session data on that domain would be saved to your browser cookies.
-  You are now in domain2 and using a form you sent a password change POST request to domain1.  
- domain1 would accept that request because after all you are still in session with them through your browser's cookies.
- it is still the same, but domain2, have intercepted your data.

How to prevent:
- domain1 would include a csrf token in their forms. Each session has unique token.
- every POST request sent to domain1 should have this token.
- if the token is correct for the session you are have. The form is accepted.
- if not, Laravel throws a 419 (Page Expired) error
```php
<form>
	@csrf //includes a hidden input tag with the csrf token as value
</form>
```
### SQL Injection

### XSS (Cross Site Scripting) 
