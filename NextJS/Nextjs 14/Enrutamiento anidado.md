
Next.js utiliza enrutamiento del sistema de archivos donde se usan **carpetas** para crear rutas anidadas. Cada carpeta representa un **segmento de ruta** que se asigna a un **segmento de URL**

![[Pasted image 20240528193829.png]]

![[Pasted image 20240528193851.png]]

## Creando la página del panel

Ejemplo : /app/dashboard/page.tsx

```tsx
export default function Page() {
  return <p>Dashboard Page</p>;
}
```


Ejemplo de como crear una ruta dentro de otra ruta :

![[Pasted image 20240528194043.png]]