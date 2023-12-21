# Setup React + Typescript & Tailwind CSS with Vite

Untuk mengatur proyek React dengan TypeScript dan Tailwind CSS menggunakan Vite, Kamu dapat mengikuti langkah-langkah berikut. Vite adalah bundler yang sangat cepat dan dapat diintegrasikan dengan React, TypeScript, dan Tailwind CSS dengan mudah.

**1. Buat Proyek Vite dengan React dan TypeScript:**

    # Buat proyek Vite dengan template "react-ts" dengan NPM
    npm create vite my-project-name --template react-ts

    OR

    # Install Vite CLI secara global (jika belum terinstall)
    npm install -g create-vite

    # Buat proyek Vite dengan template "react-ts"
    create-vite my-project-name --template react-ts

    Next >>

    # Pindah ke direktori proyek
    cd my-project-name

**2. Install Tailwind CSS:**

    # Install Tailwind CSS dan dependencies
    npm install -D tailwindcss postcss autoprefixer

    # Inisialisasi konfigurasi Tailwind CSS
    npx tailwindcss init -p

**3. Konfigurasi PostCSS:**

Buka file `postcss.config.js` dan tambahkan plugin Tailwind CSS.

    // postcss.config.js

    module.exports = {
      plugins: {
        tailwindcss: {},
        autoprefixer: {},
      },
    };

**4. Atur Styles dalam CSS atau SCSS:**

Buat file `src/styles/index.css` dan tambahkan pengaturan Tailwind CSS.

    /* src/styles/index.css */

    @import 'tailwindcss/base';
    @import 'tailwindcss/components';
    @import 'tailwindcss/utilities';

    /* Custom styles go here */

**5. Import Styles di dalam File main.tsx:**

Buka file `src/main.tsx` dan import file `styles/index.css`.

    // src/main.tsx

    import React from 'react';
    import ReactDOM from 'react-dom';
    import App from './App';
    import './styles/index.css'; // Import Tailwind CSS styles

    ReactDOM.render(
      <React.StrictMode>
        <App />
      </React.StrictMode>,
      document.getElementById('root')
    );

**6. Gunakan Tailwind CSS dalam Komponen React:**

Kamu sekarang dapat menggunakan class-class Tailwind CSS langsung dalam komponen React Kamu. Contoh:

    // src/App.tsx

    import React from 'react';

    const App: React.FC = () => {
      return (
        <div className="bg-blue-500 text-white p-4">
          <h1 className="text-2xl font-bold">Hello, Tailwind CSS!</h1>
          <p className="mt-2">This is a React app with Tailwind CSS.</p>
        </div>
      );
    };

    export default App;

**7. Jalankan Aplikasi:**

Simpan perubahan dan jalankan aplikasi menggunakan perintah:

    npm run dev

Buka browser dan akses localhost kamu, untuk melihat hasilnya.
