Particle JS API
===============

Everything returns a `promise <https://promisesaplus.com>`_ these examples are using .catch and arrow functions.

.. code-block:: html

    <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/particle-api-js@8/dist/particle.min.js"></script>
    <script>
        var particle = new Particle();
    </script>

then you can call particle.method() for example login `login <https://docs.particle.io/reference/SDKs/javascript/#login>`_ ::

    particle.login({username: 'email@example.com', password: 'pass'})
        .then((data) => {
            console.log('API call completed on promise resolve: ', data.body.access_token);
        },
        .catch((error) => {
            console.log('API call completed on promise fail: ', err);
        }
    );

Organizing as a bootstrap-vue method login, the data remembers the auth_token in a cookie for future visits ::

    particleLogin() {
        particle.login({ username: this.email, password: this.password, expires_in: this.loginExpirySeconds })
            .then((data) => {
                this.auth_token = data.body.access_token;
                this.$emit('received-auth', this.auth_token);
                this.rememberAuth();
            })
            .catch((error) => {
                console.log('Could not log in.', error);
            });
        this.password = '';
    }
