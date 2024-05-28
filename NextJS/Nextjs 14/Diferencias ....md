
#Link
 Reemplazo de 

```html
<a href="/">Home</a>
```

La etiqueta `Link` en Next.js es una herramienta poderosa para manejar la navegación en aplicaciones web. Permite crear enlaces que llevan a diferentes rutas dentro de la aplicación sin recargar la página completa, mejorando así la experiencia del usuario y el rendimiento de la aplicación. En Next.js 14, la etiqueta `Link` sigue siendo fundamental, pero puede haber algunos cambios o mejoras respecto a versiones anteriores.

```jsx
import Link from 'next/link';
```

Uso básico

```jsx
<Link href="/">
  Home
</Link>
```

**Navegación Previa Automática (Prefetching):** Next.js automáticamente hace prefetching de las rutas que están envueltas en un `Link`. Esto significa que al pasar el mouse sobre un enlace, Next.js precargará los datos de esa página para que la navegación sea instantánea. Puedes desactivar esta función si no la necesitas:

```jsx
<Link href="/about" prefetch={false}>
  About
</Link>

```


**Soporte para Enlaces Dinámicos:** Next.js soporta enlaces dinámicos usando la sintaxis de corchetes en el archivo de página (por ejemplo, `[id].js` para rutas dinámicas). Al utilizar `Link`, puedes pasar parámetros dinámicos:


```jsx
<Link href="/post/[id]" as={`/post/${post.id}`}>
  <h1 className="about-link" >{post.title}</h1>
</Link>

```

Ejemplo Completo :

```jsx
import Link from 'next/link';

const HomePage = () => {
  const posts = [
    { id: '1', title: 'First Post' },
    { id: '2', title: 'Second Post' },
  ];

  return (
    <div>
      <h1>Welcome to our site!</h1>
      <nav>
        <Link href="/about">
          <a>About Us</a>
        </Link>
        <Link href="/contact">
          <a>Contact</a>
        </Link>
      </nav>
      <div>
        <h2>Blog Posts</h2>
        {posts.map((post) => (
          <Link key={post.id} href="/post/[id]" as={`/post/${post.id}`}>
            <a>{post.title}</a>
          </Link>
        ))}
      </div>
    </div>
  );
};

export default HomePage;

```