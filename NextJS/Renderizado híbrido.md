
El renderizado híbrido en Next.js permite combinar el renderizado estático (SSG) y el renderizado del lado del servidor (SSR) dentro de una misma aplicación. Esto es útil para páginas que tienen partes que pueden ser prerenderizadas estáticamente y otras que requieren datos dinámicos.

A continuación, te explicaré cómo implementar una página híbrida en Next.js 14 utilizando tanto `getStaticProps` como `getServerSideProps`.


```js
// pages/hybrid.js

import React from 'react';

// Función para obtener datos en tiempo de compilación (SSG)
export async function getStaticProps() {
  // Simulación de una llamada a una API para obtener datos estáticos
  const staticRes = await fetch('https://jsonplaceholder.typicode.com/posts');
  const staticPosts = await staticRes.json();

  // Retorna los datos como props para ser usados en el componente
  return {
    props: {
      staticPosts,
    },
  };
}

// Función para obtener datos en tiempo de solicitud (SSR)
export async function getServerSideProps(context) {
  // Simulación de una llamada a una API para obtener datos dinámicos
  const dynamicRes = await fetch('https://jsonplaceholder.typicode.com/users');
  const dynamicUsers = await dynamicRes.json();

  // Retorna los datos como props para ser usados en el componente
  return {
    props: {
      dynamicUsers,
    },
  };
}

const HybridPage = ({ staticPosts, dynamicUsers }) => {
  return (
    <div>
      <h1>Hybrid Rendering Page</h1>
      <section>
        <h2>Static Posts (SSG)</h2>
        <ul>
          {staticPosts.map(post => (
            <li key={post.id}>
              <h3>{post.title}</h3>
              <p>{post.body}</p>
            </li>
          ))}
        </ul>
      </section>
      <section>
        <h2>Dynamic Users (SSR)</h2>
        <ul>
          {dynamicUsers.map(user => (
            <li key={user.id}>
              <h3>{user.name}</h3>
              <p>{user.email}</p>
            </li>
          ))}
        </ul>
      </section>
    </div>
  );
};

export default HybridPage;

```