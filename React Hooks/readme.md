# React Hooks

React Hook adalah sebuah fitur dalam React yang memungkinkan Kamu menggunakan state dan function-function React di dalam functional components. Sebelum adanya Hooks, pengelolaan state dan siklus hidup components hanya dapat dilakukan di dalam components class. Dengan adanya Hooks, Kamu dapat menggunakan function-function seperti `useState`, `useEffect`, dan lainnya di dalam functional components, tanpa perlu mengubah components tersebut menjadi components class.

**Beberapa Hooks yang umum digunakan:**

1. `useState`: Mengizinkan functional components memiliki state. Dengan useState, Kamu bisa mendeklarasikan variabel state dan function untuk mengubahnya.

    ```
    const [count, setCount] = useState(0);
    ```

2. `useEffect`: Digunakan untuk melakukan side effects dalam functional components. Misalnya, mengambil data dari API, berlangganan ke WebSocket, atau melakukan operasi asyncronous lainnya.

    ```
    useEffect(() => {
      // Side effects disini
      console.log('Component did mount');

      return () => {
        // Clean up side effects disini
        console.log('Component will unmount');
      };
    }, []); // [] berarti side effects hanya dijalankan sekali setelah render pertama
    ```

3. `useContext`: Digunakan untuk mengakses nilai dari React.createContext dalam functional components.

    ```
    const theme = useContext(ThemeContext);
    ```

4. `useReducer`: Digunakan untuk mengelola state kompleks dengan logika pemutakhiran yang lebih rumit.

    ```
    const [state, dispatch] = useReducer(reducer, initialState);
    ```

5. `useCallback dan useMemo`: Digunakan untuk mengoptimalkan performa dengan menghindari pembuatan ulang function atau nilai yang sama setiap kali components dire-render.

    ```
    const memoizedCallback = useCallback(() => {
      // Function yang di-memoize
    }, [dependency]);

    const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
    ```

Dengan menggunakan `React Hooks`, functional components dapat memiliki lebih banyak fitur yang sebelumnya hanya tersedia pada components class, sehingga memudahkan pengembangan dan pemeliharaan kode dalam pengembangan aplikasi React.

## Contoh Penggunaan React Hooks

Contoh sederhana penggunaan useState hook di React dengan TypeScript. Kita akan membuat components sederhana yang menyimpan dan menampilkan jumlah klik pengguna.

**1. Counter Component (Counter.tsx):**

    // Counter.tsx

    import React, { useState, FC } from 'react';

    // Create the Counter component
    const Counter: FC = () => {
      // State for the count value
      const [count, setCount] = useState<number>(0);

      // Event handler for incrementing the count
      const handleIncrement = () => {
        setCount(count + 1);
      };

      // Event handler for decrementing the count
      const handleDecrement = () => {
        setCount(count - 1);
      };

      return (
        <div>
          <p>Count: {count}</p>
          <button onClick={handleIncrement}>Increment</button>
          <button onClick={handleDecrement}>Decrement</button>
        </div>
      );
    };

    export default Counter;


Penjelasan:

- `useState`: Hook dari React untuk membuat dan mengelola state dalam functional components.
- `count`: State yang menyimpan nilai jumlah klik.
- `setCount`: Function untuk memperbarui nilai state `count`.
- `handleIncrement`: Function yang memanggil `setCount` untuk menambah nilai `count` saat tombol increment diklik.
- `handleDecrement`: Function yang memanggil `setCount` untuk mengurangi nilai `count` saat tombol decrement diklik.
- Penggunaan state dalam JSX untuk menampilkan dan memperbarui nilai `count`.

**2. Penggunaan Counter Component (App.tsx):**

    // App.tsx

    import React from 'react';
    import Counter from './Counter';

    const App: React.FC = () => {
      return (
        <div>
          <h1>React Counter Example</h1>
          <Counter />
        </div>
      );
    };

    export default App;

Penjelasan:

- Penggunaan components `Counter` dalam components induk `App`.

Dengan menggunakan `useState` hook, kita dapat dengan mudah membuat dan mengelola state dalam functional components React. Saat pengguna mengklik tombol increment atau decrement, nilai state diupdate, dan components secara otomatis dirender ulang untuk mencerminkan perubahan tersebut.
