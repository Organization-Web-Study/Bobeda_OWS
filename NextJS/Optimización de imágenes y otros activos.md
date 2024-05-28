
Next.js proporciona optimización automática de imágenes y otros activos a través del componente `next/image`. Este componente optimiza las imágenes de manera automática para mejorar el rendimiento de la aplicación. A continuación, te mostraré un ejemplo de cómo usar esta característica en Next.js 14.

```js
// pages/index.js

import Image from 'next/image';
import styles from '../styles/Home.module.css';

export default function Home() {
  return (
    <div className={styles.container}>
      <h1>Next.js Image Optimization Example</h1>
      <Image
        src="/images/nextjs-logo.png" // Ruta de la imagen en la carpeta 'public'
        alt="Next.js Logo"
        width={500}
        height={500}
        layout="responsive"
      />
    </div>
  );
}

```

Ejemplo font

```js

// pages/_app.js

import { Inter } from 'next/font/google';
import '../styles/globals.css';

const inter = Inter({
  subsets: ['latin'],
  weight: ['400', '700'],
  display: 'swap', // Mejora la carga de la fuente
});

function MyApp({ Component, pageProps }) {
  return (
    <main className={inter.className}>
      <Component {...pageProps} />
    </main>
  );
}

export default MyApp;

```