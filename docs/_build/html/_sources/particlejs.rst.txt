Particle JS API
===============

Everything returns a `promise <https://promisesaplus.com>`_ these examples are using .catch and arrow functions.

example `login <https://docs.particle.io/reference/SDKs/javascript/#login>`_ ::

    particle.login({username: 'email@example.com', password: 'pass'})
        .then((data) => {
            console.log('API call completed on promise resolve: ', data.body.access_token);
        },
        .catch((error) => {
            console.log('API call completed on promise fail: ', err);
        }
    );

login ::

    particleLogin: function() {
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
