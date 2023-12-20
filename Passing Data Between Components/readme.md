# Passing Data between Components using Props

Contoh sederhana cara melewati data antar components menggunakan property (props) di React dengan TypeScript. Kita akan membuat dua components, yaitu Parent dan Child, dimana Parent akan meneruskan data ke Child melalui property.

**1. Child Component (Child.tsx):**

    // Child.tsx

    import React, { FC } from 'react';

    // Define props interface for Child component
    interface ChildProps {
      message: string;
    }

    // Create the Child component
    const Child: FC<ChildProps> = ({ message }) => {
      return (
        <div>
          <p>Message from Parent: {message}</p>
        </div>
      );
    };

    export default Child;

Penjelasan:

- `ChildProps`: Mendefinisikan property yang diterima oleh components `Child`.
- `message`: Property yang akan digunakan untuk menerima data dari `Parent`.
- `Child`: Komponen anak yang menerima property `message` dan menampilkannya.

**2. Parent Component (Parent.tsx):**

    // Parent.tsx

    import React from 'react';
    import Child from './Child';

    // Create the Parent component
    const Parent: React.FC = () => {
      const dataToSend = "Hello from Parent";

      return (
        <div>
          <h1>Parent Component</h1>
          <Child message={dataToSend} />
        </div>
      );
    };

    export default Parent;

Penjelasan:

- `dataToSend`: Variabel yang berisi data yang akan dikirimkan ke components `Child`.
- Penggunaan components `Child` dengan memberikan property `message` yang diisi dengan nilai dari `dataToSend`.

**3. Penggunaan Parent Component (App.tsx):**

    // App.tsx

    import React from 'react';
    import Parent from './Parent';

    const App: React.FC = () => {
      return (
        <div>
          <h1>React Props Example</h1>
          <Parent />
        </div>
      );
    };

    export default App;

Penjelasan:

- Penggunaan components `Parent` dalam components induk `App`.

Dengan cara ini, data (`dataToSend`) dari components `Parent` dapat dilewatkan ke components `Child` melalui property `message`. Property ini kemudian dapat digunakan di dalam components `Child` untuk menampilkan atau melakukan operasi tertentu berdasarkan data yang diterima.
