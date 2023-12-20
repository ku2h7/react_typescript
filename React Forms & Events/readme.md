# React Forms & Events

Contoh penggunaan form (form) dan peristiwa (events) pada React dengan TypeScript. Kamu akan membuat components FormExample yang memiliki form sederhana dengan input text dan button, dan menanggapi peristiwa klik pada button.

**1. FormExample Component (FormExample.tsx):**

    // FormExample.tsx

    import React, { useState, ChangeEvent, FormEvent, FC } from 'react';

    // Define props interface
    interface FormExampleProps {
      onSubmit: (inputValue: string) => void;
    }

    // Create the FormExample component
    const FormExample: FC<FormExampleProps> = ({ onSubmit }) => {
      // State for input value
      const [inputValue, setInputValue] = useState<string>('');

      // Event handler for input change
      const handleInputChange = (event: ChangeEvent<HTMLInputElement>) => {
        setInputValue(event.target.value);
      };

      // Event handler for form submission
      const handleSubmit = (event: FormEvent<HTMLFormElement>) => {
        event.preventDefault();
        onSubmit(inputValue);
        setInputValue(''); // Clear the input after submission
      };

      return (
        <form onSubmit={handleSubmit}>
          <label>
            Enter text:
            <input type="text" value={inputValue} onChange={handleInputChange} />
          </label>
          <button type="submit">Submit</button>
        </form>
      );
    };

    export default FormExample;

Penjelasan:

- `FormExampleProps`: Mendefinisikan properti yang diterima oleh components FormExample.
- `onSubmit`: Properti berupa function yang akan dipanggil saat form dikirim.
- `useState`: Hook dari React untuk membuat dan mengelola state dalam functional components.
- `inputValue`: State yang menyimpan nilai input dari pengguna.
- `handleInputChange`: Function untuk menangani perubahan nilai pada input.
- `handleSubmit`: Function yang dipanggil saat form dikirim, mencegah pengiriman form bawaan browser, dan memanggil function `onSubmit` dengan nilai input.
- Penggunaan form dengan atribut `onSubmit` untuk menanggapi peristiwa form yang dikirim.

**2. Penggunaan FormExample Component (App.tsx):**

    // App.tsx

    import React from 'react';
    import FormExample from './FormExample';

    const App: React.FC = () => {
      // Event handler for form submission
      const handleFormSubmit = (inputValue: string) => {
        alert(`Form submitted with value: ${inputValue}`);
      };

      return (
        <div>
          <h1>React Form Example</h1>
          <FormExample onSubmit={handleFormSubmit} />
        </div>
      );
    };

    export default App;

Penjelasan:

- `handleFormSubmit`: Function yang akan dipanggil saat form dikirim, dalam contoh ini, menampilkan alert dengan nilai input.
- Penggunaan components `FormExample` dengan memberikan properti `onSubmit` yang mengacu pada function `handleFormSubmit`.

Dengan cara ini, kamu membuat components form yang dapat mengelola input pengguna dan menanggapi peristiwa klik pada button "Submit". Semua components dan peristiwa ini dijalankan dengan TypeScript untuk meningkatkan keamanan dan kejelasan code.
