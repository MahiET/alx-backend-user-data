0x02. Session authentication
=

<h2>Cookies</h2>

To access cookies you can use the cookies attribute. To set cookies you can use the set_cookie method of response objects. The cookies attribute of request objects is a dictionary with all the cookies the client transmits. If you want to use sessions, do not use the cookies directly but instead use the Sessions in Flask that add some security on top of cookies for you.

                    from flask import make_response

                    @app.route('/')
                    def index():
                   resp = make_response(render_template(...))
                   resp.set_cookie('username', 'the username')
                   return resp

<h2>Redirects and Errors</h2>

To redirect a user to another endpoint, use the redirect() function; to abort a request early with an error code, use the abort() function:

               from flask import abort, redirect, url_for

               @app.route('/')
               def index():
               return redirect(url_for('login'))

               @app.route('/login')
               def login():
               abort(401)
               this_is_never_executed()

This is a rather pointless example because a user will be redirected from the index to a page they cannot access (401 means access denied) but it shows how that works.

By default a black and white error page is shown for each error code. If you want to customize the error page, you can use the errorhandler() decorator