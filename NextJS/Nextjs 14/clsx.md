
### ¿Qué es `clsx`?

`clsx` es una pequeña biblioteca de utilidad que combina la funcionalidad de `classNames` y otras herramientas similares para manejar las clases CSS. Su principal ventaja es su sintaxis concisa y su rendimiento.


```
npm install clsx
```

```jsx
import clsx from 'clsx';

const Button = ({ primary, disabled }) => {
  return (
    <button
      className={clsx({
        'btn': true, // siempre se aplica
        'btn-primary': primary, // se aplica si `primary` es verdadero
        'btn-disabled': disabled, // se aplica si `disabled` es verdadero
      })}
    >
      Click Me
    </button>
  );
};

```