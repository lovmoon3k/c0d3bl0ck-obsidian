-   [Make Help Center](https://www.make.com/en/help/index-en.html)
-   [Tools](https://www.make.com/en/help/tools.html)
-   HTTP

The HTTP app provides various modules for communication based on [Hypertext Transfer Protocol (HTTP)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol). HTTP is the foundation of data communication for the World Wide Web. The modules enable you to download web pages and files, call webhooks and API endpoints, etc.

## Getting Started with HTTP

The right choice of the module depends on the authentication/authorization mechanism the resource you wish to access employs:

-   [Make a request](https://www.make.com/en/help/tools/http.html#make-a-request "Make a request") \- universal module primarily intended for resources not employing any type of authentication/authorization
    
-   [Make a Basic Auth request](https://www.make.com/en/help/tools/http.html#make-a-basic-auth-request "Make a Basic Auth request") - for resources employing HTTP Basic Authentication (BA)
    
-   [Make an OAuth 2.0 request](https://www.make.com/en/help/tools/http.html#make-an-oauth-2-0-request "Make an OAuth 2.0 request") - for resources employing OAuth 2.0 authorization protocol
    
-   [Make a Client Certificate Auth request](https://www.make.com/en/help/tools/http.html#make-a-client-certificate-authentication-request "Make a client certificate authentication request") - for resources employing an authorization protocol that requires a client-side certificate
    
-   [Get a file](https://www.make.com/en/help/tools/http.html#get-a-file-935242 "Get a file") \- to download a file from the specified URL
    
-   [Resolve a target URL](https://www.make.com/en/help/tools/http.html#resolve-a-target-url "Resolve a target URL") - to retrieve a target URL from the chain of HTTP redirections
    
-   [Retrieve headers](https://www.make.com/en/help/tools/http.html#retrieve-headers "Retrieve Headers") - to return headers (name and value) from the specified HTTP request module in separate bundles.
    

### Caution

The module dialog fields that are displayed in **bold** (in the Make scenario, **not** in this documentation article) are mandatory!

### Make a request

A universal module that enables you to configure an HTTP request and submit it to a server. The received HTTP response is then contained in the output bundle.

<table><tbody><tr><td><p><span><strong>Evaluate all states as errors (except for 2xx and 3xx)</strong></span></p></td><td><p>Use this option to set up error handling.</p></td></tr><tr><td><p><span><strong>URL</strong></span></p></td><td><p>Enter a URL you want to send a request to, e.g., API endpoint, website, etc.</p></td></tr><tr><td><p><span><strong>Method</strong></span></p></td><td><p>Select the HTTP method you want to use:</p><div><ul><li><p><span><strong>GET</strong></span> - to retrieve information for an entry.</p></li><li><p><span><strong>POST</strong></span> - to create a new entry.</p></li><li><p><span><strong>PUT</strong></span> - to update/replace an existing entry.</p></li><li><p><span><strong>PATCH</strong></span> - to make a partial entry update.</p></li><li><p><span><strong>DELETE</strong></span> - to delete an entry.</p></li></ul></div></td></tr><tr><td><p><span><strong>Headers</strong></span></p></td><td><p>Enter the desired request headers. For example, an authorization.</p><div dir="ltr"><h3>Caution</h3><p>By default, the request does not contain the <code>Accept</code> header. If an unexpected response is returned, try adding the <code>Accept: */*</code> header.</p></div></td></tr><tr><td><p><span><strong>Query String</strong></span></p></td><td><p>Enter the desired query key-value pairs.</p></td></tr><tr><td><p><span><strong>Body type</strong></span></p></td><td><p>HTTP Body is the data bytes transmitted in an <a href="https://en.wikipedia.org/wiki/HTTP" target="_blank" rel="noopener">HTTP</a> transaction message immediately following the <a href="https://en.wikipedia.org/wiki/List_of_HTTP_headers" target="_blank" rel="noopener">headers</a> if there are any to be used.</p><div><table><tbody><tr><td><p><span><strong>Raw</strong></span></p></td><td><p>The Raw body type is generally suitable for most HTTP body requests, even in situations where developer documentation does not specify data to send.</p><p>Specify a form of parsing the data in the Content type field.</p><p>Despite the content type selected, data is entered in any format that is stipulated or required by the developer documentation.</p></td></tr><tr><td><p><span><strong>Application/x-www-form-urlencoded</strong></span></p></td><td><p>This body type is to POST data using <code>application/x-www-form-urlencoded</code>.</p><p>For <code>application/x-www-form-urlencoded</code>, the body of the HTTP message sent to the server is essentially one query string. The keys and values are encoded in key-value pairs separated by <code>&amp;</code> and with a <code>=</code> between the key and the value. Not suitable to use with binary data (use <code>multipart/form-data</code> instead).</p><p>Example of the resulting HTTP request format: <code>field1=value1&amp;field2=value2</code></p></td></tr><tr><td><p><span><strong>Multipart/form-data</strong></span></p></td><td><p>Multipart/form-data is an HTTP multipart request used to send files and data. It is commonly used to upload files to the server.</p><p>Add fields to be sent in the request. Each field must contain <span><em>Key</em></span>-<span><em>Value</em></span> pair.</p><div><table><tbody><tr><td><p><span><strong>Text</strong></span></p></td><td><p>Enter the key and value to be sent within the request body.</p></td></tr><tr><td><p><span><strong>File</strong></span></p></td><td><p>Enter the key, and specify the source file you want to send in the request body. Map the file you want to upload from the previous module (e.g., <span><em>HTTP &gt; Get a File or Google Drive &gt; Download a File</em></span>), or enter the file name and file data manually.</p></td></tr></tbody></table></div></td></tr></tbody></table></div></td></tr><tr><td><p><span><strong>Parse response</strong></span></p></td><td><p>Enable this option to automatically parse responses and convert JSON and XML responses so you don't need to use<span><em> JSON &gt; Parse JSON</em></span> or <span><em>XML &gt; Parse XML </em></span>modules.</p><p>Before you can use parsed JSON or XML content, run the module once manually so that the module can recognize the response content and allow you to map it in subsequent modules.</p></td></tr><tr><td><p><span><strong>User name</strong></span></p></td><td><p>Enter the user name if you want to send a request using the basic auth.</p></td></tr><tr><td><p><span><strong>Password</strong></span></p></td><td><p>Enter the password if you want to send a request using the basic auth.</p></td></tr><tr><td><p><span><strong>Timeout</strong></span></p></td><td><p>Specify the request timeout in seconds (1-300). Default: 40 seconds.</p></td></tr><tr><td><p><span><strong>Share cookies with other HTTP modules</strong></span></p></td><td><p>Enable this option to share cookies from the server with all HTTP modules in your <span>scenario</span>.</p></td></tr><tr><td><p><span><strong>Self-signed certificate</strong></span></p></td><td><p>Upload your certificate if you want to use TLS using your self-signed certificate. For more details about inserting the certificate, refer to the <a href="https://www.make.com/en/help/functions/certificates-and-keys.html" title="Certificates and keys">Certificates and Keys</a> article.</p></td></tr><tr><td><p><span><strong>Reject connections that use unverified (self-signed) certificates</strong></span></p></td><td><p>Enable this option to reject connections that use unverified TLS certificates.</p></td></tr><tr><td><p><span><strong>Follow redirect</strong></span></p></td><td><p>Follows the URL redirections with 3xx responses.</p></td></tr><tr><td><p><span><strong>Follow all redirect</strong></span></p></td><td><p>Follows the URL redirections with all response codes.</p></td></tr><tr><td><p><span><strong>Disable serialization of multiple same query string keys as arrays</strong></span></p></td><td><p>By default, <span>Make</span> handles multiple values for the same URL query string parameter key as arrays (e.g., <code>www.test.com?foo=bar&amp;amp;foo=baz</code> will be converted to <code>www.test.com?foo[0]=bar&amp;amp;foo[1]=baz</code>). To disable this feature, activate this option.</p></td></tr><tr><td><p><span><strong>Request compressed content</strong></span></p></td><td><p>Enable this option to request a compressed version of the website.</p><p>Adds an <code>Accept-Encoding&nbsp;</code> header to request compressed content.</p></td></tr></tbody></table>

#### Example

Shows how to set up the module to submit a POST request with JSON payload:

To make sure your JSON is valid, you may use one of the available online services (e.g., [https://jsonlint.com/](https://jsonlint.com/)) or employ the JSON &gt; Create JSON module to create the JSON dynamically and take care of all the necessary escaping. Mixing JSON pieces with expressions and items directly in the Request content field is not recommended, as it can result in an invalid JSON.

### Make a Basic Auth request

A module that enables you to configure an HTTP request with HTTP Basic authentication and submit it to a server. The received HTTP response is then contained in the output bundle.

<table><tbody><tr><td><p><span><strong>Credentials</strong></span></p></td><td><p>Click&nbsp;<span><strong>Add</strong></span> to add your credentials (user name&nbsp;and&nbsp;password) for basic authentication.</p><div dir="ltr"><h3>Note</h3><p>You can add more credentials to easily switch between each connection.</p></div></td></tr><tr><td><p><span><strong>Evaluate all states as errors (except for 2xx and 3xx )</strong></span></p></td><td><p>Use this option to set up error handling.</p></td></tr><tr><td><p><span><strong>URL</strong></span></p></td><td><p>Enter a URL you want to send a request to, e.g., API endpoint, website, etc.</p></td></tr><tr><td><p><span><strong>Method</strong></span></p></td><td><p>Select the HTTP method you want to use:</p><div><ul><li><p><span><strong>GET</strong></span> to retrieve information for an entry.</p></li><li><p><span><strong>POST</strong></span> to create a new entry.</p></li><li><p><span><strong>PUT</strong></span> to update/replace an existing entry.</p></li><li><p><span><strong>PATCH</strong></span> to make a partial entry update.</p></li><li><p><span><strong>DELETE</strong></span> to delete an entry.</p></li></ul></div></td></tr><tr><td><p><span><strong>Headers</strong></span></p></td><td><p>Enter the desired request headers. For example, an authorization.</p><p>By default, the request does not contain the <code>Accept</code> header. If an unexpected response is returned, try adding the <code>Accept: */*</code> header.</p></td></tr><tr><td><p><span><strong>Query String</strong></span></p></td><td><p>Enter the desired query key-value pairs.</p></td></tr><tr><td><p><span><strong>Body type</strong></span></p></td><td><p>HTTP Body&nbsp;is the data bytes transmitted in an&nbsp;<a href="https://en.wikipedia.org/wiki/HTTP" target="_blank" rel="noopener">HTTP</a>&nbsp;transaction message immediately following the&nbsp;<a href="https://en.wikipedia.org/wiki/List_of_HTTP_headers" target="_blank" rel="noopener">headers</a>&nbsp;if there are any to be used.</p><div><table><tbody><tr><td><p><span><strong>Raw</strong></span></p></td><td><p>The Raw body type is generally suitable for most HTTP body requests, even in situations where developer documentation does not specify data to send.</p></td></tr><tr><td><p><span><strong>Application/x-www-form-urlencoded</strong></span></p></td><td><p>This body type is to&nbsp;POST data using <code>application/x-www-form-urlencoded</code>.</p><p>For <code>application/x-www-form-urlencoded</code>, the body of the HTTP message sent to the server is essentially one query string. The keys and values are encoded in key-value pairs separated by <code>&amp;</code> and with a <code>=</code> between the key and the value.&nbsp;Not suitable to use with binary data (use <code>multipart/form-data</code> instead).</p><p>Example of the resulting HTTP request format: <code>field1=value1&amp;field2=value2</code></p></td></tr><tr><td><p><span><strong>Multipart/form-data</strong></span></p></td><td><p>Multipart/form-data is an&nbsp;HTTP multipart&nbsp;request used to send files and data. It is commonly used to upload files to the server.</p><p>Add fields to be sent in the request. Each field must contain&nbsp;<span><em>Key</em></span>-<span><em>Value</em></span>&nbsp;pair.</p><div><table><tbody><tr><td><p><span><strong>Text</strong></span></p></td><td><p>Enter the key and value to be sent within the request body.</p></td></tr><tr><td><p><span><strong>File</strong></span></p></td><td><p>Enter the key and specify the source file you want to send in the request body.</p><p>Map the file you want to upload from the previous module (e.g.,&nbsp;<span><em>HTTP &gt;; Get a File&nbsp;or&nbsp;Google Drive &gt; Download a File</em></span>), or enter the file name and file data manually.</p></td></tr></tbody></table></div></td></tr></tbody></table></div></td></tr><tr><td><p><span><strong>Parse response</strong></span></p></td><td><p>Enable this option to automatically parse responses and convert JSON and XML responses so you don't need to use&nbsp;<span><em>JSON&nbsp;&gt;&nbsp;Parse JSON</em></span>&nbsp;or&nbsp;<span><em>XML&nbsp;&gt;&nbsp;Parse XML</em></span>&nbsp;modules.</p><p>Before you can use parsed JSON or XML content, run the module once manually so that the module can recognize the response content and allow you to map it in subsequent modules.</p></td></tr><tr><td><p><span><strong>Timeout</strong></span></p></td><td><p>Specify the request timeout in seconds (1-300). Default: 40 seconds.</p></td></tr><tr><td><p><span><strong>Share cookies with other HTTP modules</strong></span></p></td><td><p>Enable this option to share cookies from the server with all HTTP modules in your <span>scenario</span>.</p></td></tr><tr><td><p><span><strong>Self-signed certificate</strong></span></p></td><td><p>Upload your certificate if you want to use TLS using your self-signed certificate. For more details about inserting the certificate, refer to the&nbsp;<a href="https://www.make.com/en/help/functions/certificates-and-keys.html" title="Certificates and keys">Certificates and Keys</a>&nbsp;article.</p></td></tr><tr><td><p><span><strong>Reject connections that are using unverified (self-signed) certificates</strong></span></p></td><td><p>Enable this option to reject connections that are using unverified TLS certificates.</p></td></tr><tr><td><p><span><strong>Follow redirect</strong></span></p></td><td><p>Follows the URL redirections with 3xx responses.</p></td></tr><tr><td><p><span><strong>Follow all redirect</strong></span></p></td><td><p>Follows the URL redirections with all response codes.</p></td></tr><tr><td><p><span><strong>Disable serialization of multiple same query string keys as arrays</strong></span></p></td><td><p>Disable serialization of multiple same query string keys as arrays (e.g., <code>www.test.com?foo=bar&amp;foo=baz</code> will be converted to <code>www.test.com?foo[0]=bar&amp;foo[1]=baz</code> ). To disable this feature, activate this option.</p></td></tr><tr><td><p><span><strong>Request compressed content</strong></span></p></td><td><p>Enable this option to request a compressed version of the website.</p><p>Adds an <code>Accept-Encoding</code> header to request compressed content.</p></td></tr></tbody></table>

### Make an OAuth 2.0 request

In order to make an HTTP(S) request to servers that require an OAuth 2.0 authorization, you need to create an OAuth connection first.

#### Creating a Connection

1.  Create an OAuth client in the target service with which you want Make to communicate. This option is most likely to be found in the Developer section of the given service. When creating the client, you will be asked to specify a so-called `Redirect URL` (sometimes called a `Callback URL`).
    
    1.  Use the following Redirect URL: `https://www.integromat.com/oauth/cb/oauth2`.
        
        ### OAuth redirect URI domain
        
        Notice that the redirect URI starts with `https://www.integromat.com` instead of `https://www.make.com`. This is currently a known issue in Make.
        
        Make was formerly called Integromat, which means you can trust this URL as much as any Make URL.
        
        Please make sure all your OAuth redirect URIs point to `https://www.integromat.com/oauth/cb/oauth2`
        
    2.  Once you have created the client in the 3rd party service, the given service will display two keys:
        
        1.  `Client ID`
            
        2.  `Client Secret`
            
            ### Note
            
            Some services call these `App Key` and `App Secret`.
            
    3.  Make sure you save these keys. You will be asked to provide them when creating the connection in Make.
        
2.  Find the `Authorize URI` and `Token URI` in the API documentation of the given service (if the service uses implicit flow, you will need only `Authorize URI`). These are URL addresses through which Make communicates with the target service. The addresses serve for OAuth authorization.
    
    1.  Examples of Yahoo addresses:
        
        1.  Authorize URI: `https://api.login.yahoo.com/oauth2/request_auth`
            
        2.  Token URI: `https://api.login.yahoo.com/oauth2/get_token`
            
3.  If the target service uses scopes (access rights), check how the service separates individual scopes, and make sure you set the _Scope separator_ in the connection advanced settings (see below) accordingly.
    
4.  Once you have completed the steps above, you can proceed with setting up the module:
    

<table><colgroup><col><col></colgroup><tbody><tr><td><p><span><strong>Connection</strong></span></p></td><td><p>Click the <span><em>Add</em></span> button to set up the OAuth 2.0 connection for the request.</p><div><table><colgroup><col><col></colgroup><tbody><tr><td><p><span><strong>Connection name</strong></span></p></td><td><p>Enter the name of the connection.</p></td></tr><tr><td><p><span><strong>Flow type</strong></span></p></td><td><p>Select the flow for obtaining tokens.</p><div><table><tbody><tr><td><p><span><strong>Authorization Code</strong></span></p></td><td><p>Enter <span><em>Authorize URI</em></span> and <span><em>Token URI</em></span> you have retrieved from the service's API documentation.</p></td></tr><tr><td><p><span><strong>Implicit</strong></span></p></td><td><p>Enter <span><em>Authorize URI</em></span> you have retrieved from the service's API documentation.</p></td></tr></tbody></table></div></td></tr><tr><td><p><span><strong>Scope</strong></span></p></td><td><p>Add the individual scopes you will need to use. You will find this information in the given service's developer (API) documentation.</p></td></tr><tr><td><p><span><strong>Scope separator</strong></span></p></td><td><p>Select what the scopes entered above should be separated by. You will find this information in the given service's developer (API) documentation.</p><p>If the separator is not set correctly, <span>Make</span> will be unable to create the connection, and you will receive an invalid scope error.</p></td></tr><tr><td><p><span><strong>Client ID</strong></span></p></td><td><p>Enter the Client ID. The <span><em>Client ID</em></span> is provided when you create an OAuth client in the service you want to connect.</p></td></tr><tr><td><p><span><strong>Client Secret</strong></span></p></td><td><p>Enter the Client Secret. The <span><em>Client Secret</em></span> is provided when you create an OAuth client in the service you want to connect.</p></td></tr><tr><td><p><span><strong>Authorize parameters</strong></span></p></td><td><p>Enter the additional authorization request parameters as a key-value pair.</p><p>Standard parameters:</p><div><ul><li><p>response_type: <code>code</code> for <span><em>Authorization Code </em></span>flow and <code>token </code>for <span><em>Implicit flow</em></span></p></li><li><p>redirect_uri: <span><code>https://www.integromat.com/oauth/cb/oauth2</code></span></p></li><li><p>client_id: <span><em>The Client ID you entered when creating the account</em></span></p></li></ul></div></td></tr><tr><td><p><span><strong>Access token parameters</strong></span></p></td><td><p>Enter the additional access token request parameters as a key-value pair.</p><p>Standard parameters:</p><div><ul><li><p>grant_type: <code>authorization_code</code></p></li><li><p>redirect_uri: <span><code>https://www.integromat.com/oauth/cb/oauth2</code></span></p></li><li><p>client_id: <span><em>The Client ID you entered when creating the account</em></span></p></li><li><p>client_secret: <span><em>The Client Secret you entered when creating the account</em></span></p></li><li><p>code: <span><em>The code returned by the authorization request</em></span></p></li></ul></div></td></tr><tr><td><p><span><strong>Refresh token parameters</strong></span></p></td><td><p>Enter the additional refresh token request parameters as a key-value pair.</p><p>Standard parameters:</p><div><ul><li><p>grant_type: <code>refresh_token</code></p></li><li><p>refresh_token: <span><em>The Refresh token obtained together with the Access token</em></span></p></li><li><p>client_id: <span><em>The Client ID you entered when creating the account</em></span></p></li><li><p>client_secret: <span><em>The Client Secret you entered when creating the account</em></span></p></li></ul></div></td></tr><tr><td><p><span><strong>Custom Headers</strong></span></p></td><td><p>Specify the custom headers to be sent with the request, if needed.</p></td></tr><tr><td><p><span><strong>Token placement</strong></span></p></td><td><p>Select whether to send the token in the <span><em>header</em></span>, <span><em>query string</em></span>, or in both.</p></td></tr><tr><td><p><span><strong>Header token name</strong></span></p></td><td><p>Enter the name of the authorization token in the header. Default: <code>Bearer</code>.</p></td></tr><tr><td><p><span><strong>Query string parameter name</strong></span></p></td><td><p>Enter the name of the authorization token in the query string. Default: <code>access_token</code>.</p></td></tr></tbody></table></div></td></tr><tr><td><p><span><strong>Evaluate all states as errors (except for 2xx and 3xx )</strong></span></p></td><td><p>Use this option to set up error handling.</p></td></tr><tr><td><p><span><strong>URL</strong></span></p></td><td><p>Enter a URL you want to send the request to, e.g., API endpoint, website, etc.</p></td></tr><tr><td><p><span><strong>Method</strong></span></p></td><td><p>Select the HTTP method you want to use:</p><div><ul><li><p><span><strong>GET</strong></span> - to retrieve information for an entry.</p></li><li><p><span><strong>POST</strong></span> - to create a new entry.</p></li><li><p><span><strong>PUT</strong></span> - to update/replace an existing entry.</p></li><li><p><span><strong>PATCH</strong></span> - to make a partial entry update.</p></li><li><p><span><strong>DELETE</strong></span> - to delete an entry.</p></li></ul></div></td></tr><tr><td><p><span><strong>Headers</strong></span></p></td><td><p>Enter the desired request headers. For example, an authorization.</p><p>By default, the request does not contain the <code>Accept</code> header. If an unexpected response is returned, try adding the <code>Accept: */*</code> header.</p><div><p><img src="https://www.make.com/en/help/image/1621f615ccbc98.png" alt="HTTP_1.png"></p></div></td></tr><tr><td><p><span><strong>Query String</strong></span></p></td><td><p>Enter the desired query key-value pairs.</p></td></tr><tr><td><p><span><strong>Body type</strong></span></p></td><td><p>HTTP Body is the data bytes transmitted in an <a href="https://en.wikipedia.org/wiki/HTTP" target="_blank" rel="noopener">HTTP</a> transaction message immediately following the <a href="https://en.wikipedia.org/wiki/List_of_HTTP_headers" target="_blank" rel="noopener">headers</a> if there are any to be used.</p><div><table><colgroup><col><col></colgroup><tbody><tr><td><p><span><strong>Raw</strong></span></p></td><td><p>The Raw body type is generally suitable for most HTTP body requests, even in situations where developer documentation does not specify data to send.</p><p>Specify a form of parsing the data in the <span><em>Content type</em></span> field.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cd1b97.png" alt="HTTP_2.png"></p></div><p>Despite the content type selected, data is entered in any format that is stipulated or required by the developer documentation.</p></td></tr><tr><td><p><span><strong>Application/x-www-form-urlencoded</strong></span></p></td><td><p>This body type is to POST data using <code>application/x-www-form-urlencoded</code>.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cd720c.png" alt="HTTP_3.png"></p></div><p>For <code>application/x-www-form-urlencoded</code>, the body of the HTTP message sent to the server is essentially one query string. The keys and values are encoded in key-value pairs separated by <code>&amp;</code> and with a <code>=</code> between the key and the value. Not suitable to use with binary data (use <code>multipart/form-data</code> instead).</p><p>Example of the resulting HTTP request format:</p><p><code>field1=value1&amp;field2=value2</code></p></td></tr><tr><td><p><span><strong>Multipart/form-data</strong></span></p></td><td><p>Multipart/form-data is an HTTP multipart request used to send files and data. It is commonly used to upload files to the server.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cec305.png" alt="HTTP_7.png"></p></div><p>Add fields to be sent in the request. Each field must contain <span><em>Key</em></span>-<span><em>Value</em></span> pair.</p><div><table><colgroup><col><col></colgroup><tbody><tr><td><p><span><strong>Text</strong></span></p></td><td><p>Enter the key and value to be sent within the request body.</p></td></tr><tr><td><p><span><strong>File</strong></span></p></td><td><p>Enter the key and specify the source file you want to send in the request body.</p><p>Map the file you want to upload from the previous module (e.g., <span><em>HTTP &gt; Get a File</em></span> or <span><em>Google Drive &gt; Download a File</em></span>), or enter the file name and file data manually.</p></td></tr></tbody></table></div></td></tr></tbody></table></div></td></tr><tr><td><p><span><strong>Parse response</strong></span></p></td><td><p>Enable this option to automatically parse responses and convert JSON and XML responses so you don't need to use&nbsp;<span><em>JSON&nbsp;&gt;&nbsp;Parse JSON</em></span>&nbsp;or&nbsp;<span><em>XML&nbsp;&gt;&nbsp;Parse XML</em></span>&nbsp;modules.</p><p>Before you can use parsed JSON or XML content, run the module once manually so that the module can recognize the response content and allow you to map it in subsequent modules.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cdc350.png" alt="HTTP_4.png"></p></div></td></tr><tr><td><p><span><strong>Timeout</strong></span></p></td><td><p>Specify the request timeout in seconds (1-300). Default: 40 seconds.</p></td></tr><tr><td><p><span><strong>Share cookies with other HTTP modules</strong></span></p></td><td><p>Enable this option to share cookies from the server with all HTTP modules in your <span>scenario</span>.</p></td></tr><tr><td><p><span><strong>Self-signed certificate</strong></span></p></td><td><p>Upload your certificate if you want to use TLS using your self-signed certificate. For more details about inserting the certificate, refer to the <a href="https://www.make.com/en/help/functions/certificates-and-keys.html" title="Certificates and keys">Certificates and Keys</a> article.</p></td></tr><tr><td><p><span><strong>Reject connections that use unverified (self-signed) certificates</strong></span></p></td><td><p>Enable this option to reject connections that use unverified TLS certificates.</p></td></tr><tr><td><p><span><strong>Follow redirect</strong></span></p></td><td><p>Follows the URL redirections with 3xx responses.</p></td></tr><tr><td><p><span><strong>Follow all redirect</strong></span></p></td><td><p>Follows the URL redirections with all response codes.</p></td></tr><tr><td><p><span><strong>Disable serialization of multiple same query string keys as arrays</strong></span></p></td><td><p>By default, <span>Make</span> handles multiple values for the same URL query string parameter key as arrays (e.g., <code>www.test.com?foo=bar&amp;foo=baz</code>will be converted to <code>www.test.com?foo[0]=bar&amp;foo[1]=baz</code>). To disable this feature, activate this option.</p></td></tr><tr><td><p><span><strong>Request compressed content</strong></span></p></td><td><p>Enable this option to request a compressed version of the website. Adds an <code>Accept-Encoding</code> header to request compressed content.</p></td></tr></tbody></table>

### Make a client certificate authentication request

Makes an HTTP(S) request to servers that require a client certificate authorization.

<table><colgroup><col><col></colgroup><tbody><tr><td><p><span><strong>Credentials</strong></span></p></td><td><p>Click the <span><em>Add</em></span> button to add your credentials (<span><em>certificate</em></span>) for client certificate authorization.</p><p>Provide the certificate you want to use for authorization. For more details about inserting a certificate, refer to the <a href="https://www.make.com/en/help/functions/certificates-and-keys.html" title="Certificates and keys">Certificates and Keys</a> article.</p></td></tr><tr><td><p><span><strong>Evaluate all states as errors (except for 2xx and 3xx )</strong></span></p></td><td><p>Use this option to set up error handling.</p></td></tr><tr><td><p><span><strong>URL</strong></span></p></td><td><p>Enter a URL you want to send a request to, e.g., API endpoint, website, etc.</p></td></tr><tr><td><p><span><strong>Method</strong></span></p></td><td><p>Select the HTTP method you want to use:</p><div><ul><li><p>GET - to retrieve information for an entry.</p></li><li><p>POST - to create a new entry.</p></li><li><p>PUT - to update/replace an existing entry.</p></li><li><p>PATCH - to make a partial entry update.</p></li><li><p>DELETE - to delete an entry.</p></li></ul></div></td></tr><tr><td><p><span><strong>Headers</strong></span></p></td><td><p>Enter the desired request headers. For example, an authorization.</p><p>By default, the request does not contain the <code>Accept</code> header. If an unexpected response is returned, try adding the <code>Accept: */*</code> header.</p><div><p><img src="https://www.make.com/en/help/image/1621f615ccbc98.png" alt="HTTP_1.png"></p></div></td></tr><tr><td><p><span><strong>Query String</strong></span></p></td><td><p>Enter the desired query key-value pairs.</p></td></tr><tr><td><p><span><strong>Body type</strong></span></p></td><td><p>HTTP Body is the data bytes transmitted in an <a href="https://en.wikipedia.org/wiki/HTTP" target="_blank" rel="noopener">HTTP</a> transaction message immediately following the <a href="https://en.wikipedia.org/wiki/List_of_HTTP_headers" target="_blank" rel="noopener">headers</a> if there are any to be used.</p><div><table><colgroup><col><col></colgroup><tbody><tr><td><p><span><strong>Raw</strong></span></p></td><td><p>The Raw body type is generally suitable for most HTTP body requests, even in situations where developer documentation does not specify data to send.</p><p>Specify a form of parsing the data in the <span><em>Content type</em></span> field.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cd1b97.png" alt="HTTP_2.png"></p></div><p>Despite the content type selected, data is entered in any format that is stipulated or required by the developer documentation.</p></td></tr><tr><td><p><span><strong>Application/x-www-form-urlencoded</strong></span></p></td><td><p>This body type is to POST data using <code>application/x-www-form-urlencoded</code>.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cd720c.png" alt="HTTP_3.png"></p></div><p>For <code>application/x-www-form-urlencoded</code>, the body of the HTTP message sent to the server is essentially one query string. The keys and values are encoded in key-value pairs separated by <code>&amp;</code> and with a <code>=</code> between the key and the value. Not suitable to use with binary data (use <code>multipart/form-data</code> instead).</p><p>Example of the resulting HTTP request format:</p><p><code>field1=value1&amp;field2=value2</code></p></td></tr><tr><td><p><span><strong>Multipart/form-data</strong></span></p></td><td><p>Multipart/form-data is an HTTP multipart request used to send files and data. It is commonly used to upload files to the server.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cec305.png" alt="HTTP_7.png"></p></div><p>Add fields to be sent in the request. Each field must contain <span><em>Key</em></span>-<span><em>Value</em></span> pair.</p><div><table><colgroup><col><col></colgroup><tbody><tr><td><p><span><strong>Text</strong></span></p></td><td><p>Enter the key and value to be sent within the request body.</p></td></tr><tr><td><p><span><strong>File</strong></span></p></td><td><p>Enter the key and specify the source file you want to send in the request body.</p><p>Map the file you want to upload from the previous module (e.g., <span><em>HTTP &gt; Get a File</em></span> or <span><em>Google Drive &gt; Download a File</em></span>), or enter the file name and file data manually.</p></td></tr></tbody></table></div></td></tr></tbody></table></div></td></tr><tr><td><p><span><strong>Parse response</strong></span></p></td><td><p>Enable this option to automatically parse responses and convert JSON and XML responses so you don't need to use<span><em> JSON &gt; Parse JSON</em></span> or <span><em>XML &gt; Parse XML </em></span>modules.</p><p>Before you can use parsed JSON or XML content, run the module once manually so that the module can recognize the response content and allow you to map it in subsequent modules.</p><div><p><img src="https://www.make.com/en/help/image/1621f615cdc350.png" alt="HTTP_4.png"></p></div></td></tr><tr><td><p><span><strong>Timeout</strong></span></p></td><td><p>Specify the request timeout in seconds (1-300). Default: 40 seconds.</p></td></tr><tr><td><p><span><strong>Share cookies with other HTTP modules</strong></span></p></td><td><p>Enable this option to share cookies from the server with all HTTP modules in your <span>scenario</span>.</p></td></tr><tr><td><p><span><strong>Self-signed certificate</strong></span></p></td><td><p>Upload your certificate if you want to use TLS using your self-signed certificate. For more details about inserting the certificate, refer to the <a href="https://www.make.com/en/help/functions/certificates-and-keys.html" title="Certificates and keys">Certificates and Keys</a> article.</p></td></tr><tr><td><p><span><strong>Reject connections that are using unverified (self-signed) certificates</strong></span></p></td><td><p>Enable this option to reject connections that are using unverified TLS certificates.</p></td></tr><tr><td><p><span><strong>Follow redirect</strong></span></p></td><td><p>Follows the URL redirections with 3xx responses.</p></td></tr><tr><td><p><span><strong>Follow all redirect</strong></span></p></td><td><p>Follows the URL redirections with all response codes.</p></td></tr><tr><td><p><span><strong>Disable serialization of multiple same query string keys as arrays</strong></span></p></td><td><p>By default, <span>Make</span> handles multiple values for the same URL query string parameter key as arrays (e.g., <code>www.test.com?foo=bar&amp;foo=baz</code> will be converted to <code>www.test.com?foo[0]=bar&amp;foo[1]=baz</code>). To disable this feature, activate this option.</p></td></tr><tr><td><p><span><strong>Request compressed content</strong></span></p></td><td><p>Enable this option to request a compressed version of the website. Adds an <code>Accept-Encoding</code> header to request compressed content.</p></td></tr></tbody></table>

### Get a file

Downloads a file from the specified URL.

<table><tbody><tr><td><p><span><strong>URL</strong></span></p></td><td><p>Enter the URL of the file you want to download. After the file is downloaded, you can further process the file (map the file data) using other modules in the <span>scenario</span>.</p></td></tr></tbody></table>

### Resolve a target URL

Enter the URL of the file you want to download. After the file is downloaded, you can further process the file (map the file data) using other modules in the

<table><tbody><tr><td><p><span><strong>URL</strong></span></p></td><td><p>Enter the URL you want to resolve, e.g.,&nbsp;<span><em>https://bit.ly/2FbUoRt</em></span></p></td></tr><tr><td><p><span><strong>Method</strong></span></p></td><td><p>Select the method you want to use.</p></td></tr></tbody></table>

## Generating JSON Web Tokens (JWT)

It is possible to generate a [JWT token](http://jwt%20token/) using the HS256 algorithm with the help of built-in functions:

**Header:**

Code for copy & paste:

```
{{replace(replace(replace(base64("{""alg"":""HS256"",""typ"":""JWT""}"); "/=/g"; emptystring); "/\+/g"; "-"); "/\//g"; "_")}}
```

**Payload:**

Code for copy & paste:

```
{{replace(replace(replace(base64("{""iss"":""key"",""exp"":" + (timestamp + 60) + "}"); "/=/g"; emptystring); "/\+/g"; "-"); "/\//g"; "_")}}
```

**Token:**

Code for copy & paste:

```
{{11.header}}.{{12.payload}}.{{replace(replace(replace(sha256(11.header + "." + 12.payload; "base64"; 16.secret); "/=/g"; emptystring); "/\+/g"; "-"); "/\//g"; "_")}}
```