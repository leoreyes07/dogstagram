# 🐾 Dogstagram

**Dogstagram** is a high-performance, responsive web application designed for dog enthusiasts. Built with **Svelte** and **Vite**, it offers a seamless social media-style experience, allowing users to browse and discover various dog breeds with lightning-fast interactions.

## 🚀 Key Features

* **Reactive Gallery:** A fluid feed of dog images that updates instantly using Svelte's built-in reactivity.
* **Breed Discovery:** Integration with [The Dog API](https://thedogapi.com/) to fetch real-time breed data and high-quality imagery.
* **Performance First:** Compiled with **Vite** for a near-instant development experience and a tiny production footprint.
* **Responsive UI:** Mobile-first design ensures a great browsing experience on any device.
* **Modular Styling:** Clean and maintainable **SCSS** architecture using modern CSS patterns.

## 🛠️ Technology Stack

* **Framework:** [Svelte](https://svelte.dev/) (Zero-runtime overhead)
* **Build Tool:** [Vite](https://vitejs.dev/) (Fast HMR and bundling)
* **State Management:** Svelte Stores (Native, lightweight state)
* **Styling:** SCSS / SASS
* **API Integration:** Fetch API

## 📦 Installation & Setup

To get a local copy up and running, follow these simple steps:

1.  **Clone the repo:**
    ```bash
    git clone [https://github.com/leoreyes07/dogstagram.git](https://github.com/leoreyes07/dogstagram.git)
    ```
2.  **Install dependencies:**
    ```bash
    npm install
    ```
3.  **Launch development server:**
    ```bash
    npm run dev
    ```
4.  **Build for production:**
    ```bash
    npm run build
    ```

## 🏗️ Architecture

This project emphasizes **clean code** and **modularity**:
* **Component-Driven:** Each UI element is a self-contained Svelte component.
* **Scoped Styles:** SCSS is scoped to components to prevent style leakage and ensure maintainability.
* **Efficient Data Flow:** Leveraging Svelte's reactive declarations (`$:`) to handle API data transformations without extra boilerplate.

---
Developed by [Leo Reyes](https://github.com/leoreyes07)
