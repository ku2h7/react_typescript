# Create Form with Formik & Yup Validation

`Formik` adalah perpustakaan (library) untuk mengelola formulir (forms) di React. Formik menyediakan solusi yang kuat dan mudah digunakan untuk menangani logika formulir seperti manajemen nilai, validasi, sentuhan (touch) dan perubahan (change) pada formulir. Formik juga memfasilitasi integrasi formulir dengan mudah dan mendukung TypeScript secara alami.

`Yup` adalah perpustakaan validasi untuk JavaScript dan TypeScript. Yup memungkinkan Anda mendefinisikan skema validasi yang kuat untuk memeriksa apakah data memenuhi persyaratan tertentu. Yup bekerja dengan baik dengan Formik dan dapat digunakan untuk menentukan validasi pada data formulir.

Berikut adalah contoh penggunaan Formik dan Yup dalam proyek React dengan TypeScript:

**1. Instalasi Formik dan Yup:**

    # Install Formik dan Yup
    npm install formik yup @types/yup

**2. Contoh Penggunaan Formik dan Yup dalam Components Form (FormExample.tsx):**

    // FormExample.tsx

    import React from 'react';
    import { Formik, Field, Form, ErrorMessage } from 'formik';
    import * as Yup from 'yup';

    // Define validation schema using Yup
    const validationSchema = Yup.object({
      name: Yup.string().required('Name is required'),
      email: Yup.string().email('Invalid email format').required('Email is required'),
    });

    // Define initial form values
    const initialValues = {
      name: '',
      email: '',
    };

    // Define the onSubmit function
    const onSubmit = (values: any) => {
      console.log('Form submitted with values:', values);
    };

    const FormExample: React.FC = () => {
      return (
        <Formik
          initialValues={initialValues}
          validationSchema={validationSchema}
          onSubmit={onSubmit}
        >
          <Form>
            <div>
              <label htmlFor="name">Name:</label>
              <Field type="text" id="name" name="name" />
              <ErrorMessage name="name" component="div" />
            </div>

            <div>
              <label htmlFor="email">Email:</label>
              <Field type="text" id="email" name="email" />
              <ErrorMessage name="email" component="div" />
            </div>

            <button type="submit">Submit</button>
          </Form>
        </Formik>
      );
    };

    export default FormExample;

Penjelasan:

- `validationSchema`: Membuat skema validasi menggunakan Yup. Dalam contoh ini, kita memvalidasi bahwa `name` dan `email` diperlukan, dan format email harus benar.
- `initialValues`: Menyediakan nilai awal formulir.
- `onSubmit`: Function yang akan dipanggil saat formulir dikirimkan.
- `Formik`: Menggunakan components Formik sebagai wadah utama untuk formulir. Property `initialValues`, `validationSchema`, dan `onSubmit` disetel di sini.
- `Field`: Components yang digunakan untuk membuat input dalam formulir. Properti type, id, dan name didefinisikan.
- `ErrorMessage`: Components untuk menampilkan pesan kesalahan jika validasi gagal.
- `Form`: Components yang mengelilingi semua elemen formulir.
- Tombol `Submit` yang memicu function `onSubmit` saat diklik.

**3. Penggunaan FormExample Component (App.tsx):**

    // App.tsx

    import React from 'react';
    import FormExample from './FormExample';

    const App: React.FC = () => {
      return (
        <div>
          <h1>React Formik and Yup Example</h1>
          <FormExample />
        </div>
      );
    };

    export default App;

Penjelasan:

- Penggunaan components `FormExample` dalam components induk `App`.

Dengan penggunaan `Formik` dan `Yup`, Anda dapat dengan mudah menangani logika formulir, validasi, dan mengelola state formulir dengan lebih efisien dalam aplikasi React dengan TypeScript.
