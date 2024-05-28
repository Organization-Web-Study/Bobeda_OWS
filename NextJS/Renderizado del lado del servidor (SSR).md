
El renderizado del lado del servidor (SSR, por sus siglas en inglés) es una técnica en la cual la generación del HTML de una página web se realiza en el servidor en lugar de en el cliente (navegador). Esto puede ofrecer varias ventajas en términos de rendimiento y optimización para motores de búsqueda (SEO). A continuación, se detalla cómo funciona y cuáles son sus beneficios:

### Cómo Funciona el SSR en Next.js

1. **Petición Inicial**: Cuando un usuario solicita una página web, el servidor recibe la petición.
2. **Generación del HTML**: El servidor ejecuta el código de React, renderizando la página en HTML con todos los datos necesarios.
3. **Envío del HTML al Cliente**: El HTML generado se envía al navegador del usuario.
4. **Hidratación**: Una vez que el HTML llega al cliente, React toma el control del HTML estático y lo "hidrata", convirtiéndolo en una aplicación interactiva. Esto significa que React añade la funcionalidad completa de la aplicación, incluyendo eventos y estado.

### Beneficios del SSR

1. **Mejora del Tiempo de Carga Inicial**: Dado que el HTML completo se envía al cliente, el usuario puede ver el contenido de la página más rápidamente en comparación con el renderizado del lado del cliente, donde se necesita descargar y ejecutar JavaScript antes de renderizar la página.
2. **Mejor SEO**: Los motores de búsqueda pueden indexar el contenido de la página más eficientemente, ya que reciben un HTML completamente renderizado. Esto es crucial para mejorar la visibilidad en los resultados de búsqueda.
3. **Mejor Compartición en Redes Sociales**: Las plataformas de redes sociales pueden extraer metadatos y contenido más fácilmente de las páginas renderizadas en el servidor, mejorando la presentación al compartir enlaces.
4. **Manejo de Datos Iniciales**: SSR puede ser útil para aplicaciones que necesitan cargar datos desde un servidor antes de renderizar la página. Los datos se pueden recuperar y renderizar en el servidor, proporcionando una página completa al cliente.

### Implementación de SSR en Next.js

En Next.js, el SSR se implementa utilizando una función especial llamada `getServerSideProps`. Aquí hay un ejemplo básico:

```js
// pages/ssr.js

import React from 'react';

// Función para obtener datos del servidor antes de renderizar la página
export async function getServerSideProps() {
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

const SSRPage = ({ posts }) => {
  return (
    <div>
      <h1>Server-Side Rendered Page</h1>
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

export default SSRPage;

```