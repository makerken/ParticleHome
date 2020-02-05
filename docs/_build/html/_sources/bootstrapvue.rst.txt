BootstrapVue
============

 `<https://bootstrap-vue.js.org/docs/reference/starter-templates/>`_ 

.. code-block:: html

    <!doctype html>
    <html lang="en">
        <head>
            <!-- Required meta tags -->
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

            <!-- Bootstrap CSS -->
            <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

            <title>Bootstrap</title>
        </head>

        <body>
            <div class="container">
                <h1>Particle Home</h1>
            </div>
        </body>

    </html>

Five parts to use Vue

1. include
2. declare an id in the body
3. use that id to start vue
4. data in named in Vue
5. link to body using {{ data }}

.. code-block:: html

    <!doctype html>
    <html lang="en">
        <head>
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

            <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

            <!-- #1 Production Vue -->
            <script src="https://cdn.jsdelivr.net/npm/vue"></script>

            <title>Bootstrap</title>
        </head>

        <body>
            <!-- #2 -->
            <div id="app">
                <div class="container">
                    <h1>Particle Home</h1>
                    <!-- #5 -->
                    {{ temperature }}
                </div>
            </div>
        </body>

        <script>
            // #3
            var app = new Vue({
                el: '#app',
                data: {
                    // #4
                    temperature: 19.5
                }
            })
        </script>

    </html>

add methods, router, html templates, and v-for
