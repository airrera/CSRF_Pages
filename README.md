# CSRF_Pages
Simple HTML/JavaScript pages that could be used to exploit CSRF issues

## Keep in mind

When you try a CSRF POST or PUT with JSON content:

1 - In order to work the server must have a CORS misconfiguration like: 

- ACAO: '*' 
- ACAC: 'true'

**Note**: It will not work with NO ACAO header or ACAO: null an empty ACAO.

Because is not considered a 'simple' request, the browser will initiate a preflight OPTIONS request first - and then the original POST request will be sent with the proper Content-type value header (application/json)

2 - Similar CORS scenario will occur when the target reflects the Origin header from the request in the ACAO header (Reflected Origin issue):

- ACAO: 'malicious_domain' 
- ACAC: 'true'

3 - No CORS misconfiguration but target is not checking the Content-type: 

By using the option 'no-cors' in the fetch method (this only works with fetch) it will send the POST request but with "Content-type: text/plain;". 

### References:

- https://blog.vnaik.com/posts/web-attacks.html
- https://crashtest-security.com/same-origin-policy-sop
- https://portswigger.net/web-security/cors/same-origin-policy

##### CORS:
- https://www.packetlabs.net/posts/cross-origin-resource-sharing-cors
- https://www.baeldung.com/cs/cors-preflight-requests

