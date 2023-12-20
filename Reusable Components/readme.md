# Reusable Components

Contoh sederhana dari reusable components menggunakan React dengan TypeScript. Kita akan membuat dua komponen sederhana, yaitu `Button` dan `Alert`.

**1. Button Component (Button.tsx):**

    // Button.tsx

    import React, { ReactNode, FC, MouseEvent } from 'react';

    // Define the props interface
    interface ButtonProps {
      onClick: (event: MouseEvent<HTMLButtonElement>) => void;
      children: ReactNode;
    }

    // Create the Button component
    const Button: FC<ButtonProps> = ({ onClick, children }) => {
      return (
        <button onClick={onClick}>
          {children}
        </button>
      );
    };

    export default Button;

Penjelasan:

- `ButtonProps`: Mendefinisikan properti yang diterima oleh komponen tombol.
- `onClick`: Merupakan fungsi yang akan dipanggil ketika tombol diklik.
- `children`: Properti ini mengacu pada elemen-elemen yang akan ditampilkan di dalam tombol.
- `Button`: Komponen tombol sendiri, menerima properti dan menggunakan fungsi `onClick` saat tombol diklik.

**2. Alert Component (Alert.tsx):**

    // Alert.tsx

    import React, { FC, ReactNode } from 'react';

    // Define the props interface
    interface AlertProps {
      type: 'success' | 'error';
      children: ReactNode;
    }

    // Create the Alert component
    const Alert: FC<AlertProps> = ({ type, children }) => {
      return (
        <div className={`alert ${type}`}>
          {children}
        </div>
      );
    };

    export default Alert;

Penjelasan:

- `AlertProps`: Mendefinisikan properti yang diterima oleh komponen peringatan.
- `type`: Properti ini menentukan jenis peringatan, apakah 'success' atau 'error'.
- `children`: Properti ini mengacu pada elemen-elemen yang akan ditampilkan di dalam peringatan.
- `Alert`: Komponen peringatan sendiri, menerima properti dan menggunakan kelas CSS berdasarkan jenis peringatan.

**3. Penggunaan Komponen-Komponen Reusable (App.tsx):**

    // App.tsx

    import React from 'react';
    import Button from './Button';
    import Alert from './Alert';

    const App: React.FC = () => {
      const handleButtonClick = () => {
        alert('Button clicked!');
      };

      return (
        <div>
          <Button onClick={handleButtonClick}>Click me</Button>
          <Alert type="success">Operation successful!</Alert>
          <Alert type="error">Error occurred!</Alert>
        </div>
      );
    };

    export default App;

Penjelasan:

- `andleButtonClick`: Fungsi yang akan dipanggil saat tombol diklik, dalam contoh ini menampilkan alert.
- Penggunaan komponen `Button` dan `Alert` dengan memberikan properti yang sesuai.

Dengan cara ini, Kamu dapat menggunakan komponen-komponen ini di berbagai bagian dalam aplikasi Kamu dan mengubah perilaku atau tampilannya dengan mudah dengan memberikan properti yang sesuai. Ini memungkinkan penggunaan kembali (reusability) dan mempermudah pemeliharaan kode.
