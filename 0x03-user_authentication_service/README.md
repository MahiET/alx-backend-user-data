0x03. User authentication service
=

<h2>JSON Response Content</h2>

In case the JSON decoding fails, r.json() raises an exception. For example, if the response gets a 204 (No Content), or if the response contains invalid JSON, attempting r.json() raises requests.exceptions.JSONDecodeError. This wrapper exception provides interoperability for multiple exceptions that may be thrown by different python versions and json serialization libraries.

It should be noted that the success of the call to r.json() does not indicate the success of the response. Some servers may return a JSON object in a failed response (e.g. error details with HTTP 500). Such JSON will be decoded and returned. To check that a request is successful, use r.raise_for_status() or check r.status_code is what you expect.

<h2>Custom Headers</h2>


If you’d like to add HTTP headers to a request, simply pass in a dict to the headers parameter.

For example, we didn’t specify our user-agent in the previous example:

             url = 'https://api.github.com/some/endpoint'
             headers = {'user-agent': 'my-app/0.0.1'}

             r = requests.get(url, headers=headers)

* Authorization headers set with headers= will be overridden if credentials are specified in .netrc, which in turn will be overridden by the auth= parameter. Requests will search for the netrc file at ~/.netrc, ~/_netrc, or at the path specified by the NETRC environment variable.

* Authorization headers will be removed if you get redirected off-host.

* Proxy-Authorization headers will be overridden by proxy credentials provided in the URL.

* Content-Length headers will be overridden when we can determine the length of the content.