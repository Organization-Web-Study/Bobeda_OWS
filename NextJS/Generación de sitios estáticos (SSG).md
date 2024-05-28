
La generación de sitios estáticos (SSG, por sus siglas en inglés) es una técnica donde las páginas se generan en tiempo de compilación en lugar de en tiempo de solicitud. Next.js facilita la implementación de SSG mediante la función `getStaticProps`.

A continuación, te mostraré un ejemplo completo de cómo implementar SSG en Next.js 14.

```js
// pages/static.js

import React from 'react';

// Función para obtener datos en tiempo de compilación
export async function getStaticProps() {
  // Simulación de una llamada a una API para obtener datos
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const data = await res.json();

  // Retorna los datos como props para ser usados en el componente
  return {
    props: {
      posts: data,
    },
  };
}

const StaticPage = ({ posts }) => {
  return (
    <div>
      <h1>Static Site Generation Page</h1>
      <ul>
        {posts.map(post => (
          <li key={post.id}>
            <h2>{post.title}</h2>
            <p>{post.body}</p>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default StaticPage;

```