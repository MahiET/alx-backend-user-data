0x01. Basic authentication
=

<h2>Authorization</h2>

The Authorization header is usually, but not always, sent after the user agent first attempts to request a protected resource without credentials. The server responds with a 401 Unauthorized message that includes at least one WWW-Authenticate header. This header indicates what authentication schemes can be used to access the resource (and any additional information needed by the client to use them). The user-agent should select the most secure authentication scheme that it supports from those offered, prompt the user for their credentials, and then re-request the resource (including the encoded credentials in the Authorization header).

<h2>Flask</h2>

Flask is a lightweight WSGI web application framework. It is designed to make getting started quick and easy, with the ability to scale up to complex applications. It began as a simple wrapper around Werkzeug and Jinja and has become one of the most popular Python web application frameworks.

                       # save this as app.py
                       from flask import Flask, request
                       from markupsafe import escape

                       app = Flask(__name__)

                       @app.route('/')
                       def hello():
                       name = request.args.get("name", "World")
                       return f'Hello, {escape(name)}!'

