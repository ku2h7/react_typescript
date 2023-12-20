# Manage State in React Components

Untuk mengelola state di React menggunakan class components dengan TypeScript, Kamu dapat menggunakan pendekatan tradisional dengan menggunakan `this.state` dan `this.setState`. Saya akan memberikan contoh sederhana penggunaan state dengan class component dan bagaimana menggunakan `prevState` dalam `setState`.

**1. Counter Component (Counter.tsx):**

    // Counter.tsx

    import React, { Component } from 'react';

    // Define state interface
    interface CounterState {
      count: number;
    }

    // Create the Counter component
    class Counter extends Component<{}, CounterState> {
      // Inisialisasi state
      state: CounterState = {
        count: 0,
      };

      // Event handler untuk increment
      handleIncrement = () => {
        this.setState((prevState) => ({
          count: prevState.count + 1,
        }));
      };

      // Event handler untuk decrement
      handleDecrement = () => {
        this.setState((prevState) => ({
          count: prevState.count - 1,
        }));
      };

      render() {
        return (
          <div>
            <p>Count: {this.state.count}</p>
            <button onClick={this.handleIncrement}>Increment</button>
            <button onClick={this.handleDecrement}>Decrement</button>
          </div>
        );
      }
    }

    export default Counter;

Penjelasan:

- `CounterState`: Mendefinisikan bentuk state yang akan digunakan oleh components.
- `state`: Inisialisasi state awal dengan nilai awal count.
- `handleIncrement` dan `handleDecrement`: Menggunakan `this.setState` dengan menggunakan `prevState` untuk memastikan pembaruan state yang benar.
- Penggunaan `this.state.count` untuk mendapatkan nilai `count` saat ini.

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

Dalam contoh ini, state count dikelola di dalam components class Counter. Ketika button increment atau decrement diklik, kita menggunakan this.setState untuk memperbarui nilai count dengan menggunakan prevState untuk memastikan operasi pembaruan yang aman secara asyncronous. Ini membantu mencegah konflik jika terjadi beberapa pembaruan state secara bersamaan.
