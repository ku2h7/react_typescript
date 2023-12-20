# Handling Events & Input in React Components

Berikut adalah contoh sederhana cara menangani peristiwa pengguna (user events) dan input di components React dengan TypeScript. Kamu akan membuat components Form yang memiliki input text dan button yang akan menangani peristiwa klik.

**1. Form Component (Form.tsx):**

    // Form.tsx

    import React, { useState, ChangeEvent, MouseEvent, FC } from 'react';

    // Define the props interface
    interface FormProps {
      onSubmit: (inputValue: string) => void;
    }

    // Create the Form component
    const Form: FC<FormProps> = ({ onSubmit }) => {
      // State for input value
      const [inputValue, setInputValue] = useState<string>('');

      // Event handler for input change
      const handleInputChange = (event: ChangeEvent<HTMLInputElement>) => {
        setInputValue(event.target.value);
      };

      // Event handler for form submission
      const handleSubmit = (event: MouseEvent<HTMLButtonElement>) => {
        event.preventDefault();
        onSubmit(inputValue);
        setInputValue(''); // Clear the input after submission
      };

      return (
        <form>
          <label>
            Enter text:
            <input type="text" value={inputValue} onChange={handleInputChange} />
          </label>
          <button onClick={handleSubmit}>Submit</button>
        </form>
      );
    };

    export default Form;

Penjelasan:

- `FormProps`: Mendefinisikan property yang diterima oleh components Form, dalam hal ini, sebuah function `onSubmit` yang akan dipanggil saat from dikirim.
- `useState`: Hook dari React untuk membuat dan mengelola state dalam components functiononal.
- `inputValue`: State yang menyimpan nilai input dari pengguna.
- `handleInputChange`: Function untuk menangani perubahan nilai pada input.
- `handleChange`: Function yang memperbarui `inputValue` dengan nilai baru saat pengguna mengubah input.
- `handleSubmit`: Function yang dipanggil saat button diklik, mencegah pengiriman from bawaan browser, dan memanggil function `onSubmit` dengan nilai input.
- Penggunaan input dan button dengan property dan peristiwa yang sesuai.

**2. Penggunaan Form Component (App.tsx):**

    // App.tsx

    import React from 'react';
    import Form from './Form';

    const App: React.FC = () => {
      // Event handler for form submission
      const handleFormSubmit = (inputValue: string) => {
        alert(`Form submitted with value: ${inputValue}`);
      };

      return (
        <div>
          <h1>React Form Example</h1>
          <Form onSubmit={handleFormSubmit} />
        </div>
      );
    };

    export default App;

Penjelasan:

- `handleFormSubmit`: Function yang akan dipanggil saat from dikirim, dalam contoh ini, menampilkan alert dengan nilai input.
- Penggunaan components `Form` dengan memberikan property `onSubmit` yang mengacu pada function `handleFormSubmit`.

Dengan cara ini, kamu membuat components form yang dapat mengelola input pengguna dan menanggapi peristiwa klik pada button. Semua components dan peristiwa ini dijalankan dengan TypeScript untuk meningkatkan keamanan dan kejelasan code.
