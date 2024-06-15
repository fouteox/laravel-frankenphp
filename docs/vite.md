# Vite

To take advantage of the benefits of Vite, follow the instructions below.

If you haven't already, start the project:

    docker compose up --pull always -d --wait

Check that the laravel home page appears correctly: [https://localhost](https://localhost)

Run:
    
    docker compose exec php npm install @vitejs/plugin-basic-ssl --save-dev

Update your vite.config.js:
```js
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import basicSsl from '@vitejs/plugin-basic-ssl'

export default defineConfig({
    server: {
        https: true,
        host: '0.0.0.0',
        hmr: {
            host: 'localhost',
        }
    }, 
    plugins: [
        basicSsl({
            /** name of certification */
            name: 'WhatYouWant',
            /** custom trust domains */
            domains: ['localhost'],
            /** custom certification directory (from the project root for example) */
            certDir: './cert'
        }),
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
});
```
Just before `</head>` balise on `resources/views/welcome.blade.php`, add this:
```javascript
@vite(['resources/css/app.css', 'resources/js/app.js'])
```
Run:

    docker compose exec php npm run dev

Accept certificate: [https://localhost:5173](https://localhost:5173)

Enjoy, you have vite refresh: [https://localhost](https://localhost)

Of course, you can also use it with any starter kit.
