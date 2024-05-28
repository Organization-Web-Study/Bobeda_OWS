Cuando se crea un proyecto en nextjs y se usa Tailwindcss
por defecto se crea un archivo llamado global.css

debe estar importado en el layourt principal (que se encuentra en la carpeta APP)

```tsx
import '@/app/ui/global.css';
 
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```


dentro de ese archivo es necesario dejar las tres lineas , configuración de Tailwindcss

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

de esta forma podemos usar tailwind css 

```tsx
<h1 className="text-blue-500">I'm blue!</h1>
```


CSS puro

También podemos usar CSS puro combinado o no con Tailwindcss

se recomienda crear un archivo llamado "home.module.css" 

```css
.shape {
  height: 0;
  width: 0;
  border-bottom: 30px solid black;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```

```tsx 
//cualquier ruta :

import AcmeLogo from '@/app/ui/acme-logo';
import { ArrowRightIcon } from '@heroicons/react/24/outline';
import Link from 'next/link';
import styles from '@/app/ui/home.module.css'; /// importamos el archivo css
 
export default function Page() {
  return (
    <main className="flex min-h-screen flex-col p-6">
      <div className={styles.shape} />
    // ...
  )
} 

```