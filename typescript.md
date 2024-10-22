# Conseptos básicos de TypeScript

TypeScript es un lenguaje de programación que es un superconjunto de JavaScript. Esto significa que cualquier código JavaScript es válido en TypeScript, pero no al revés. TypeScript añade características adicionales a JavaScript, como el tipado estático, interfaces, clases, entre otras.

## Tipado estático

El tipado estático es una de las características más importantes de TypeScript. Esto significa que se pueden definir los tipos de las variables, parámetros y funciones. Por ejemplo, si se define una variable de tipo `number`, solo se podrá asignar valores numéricos a esa variable.

```typescript
let numero: number = 5;
```

## Interfaces

Las interfaces son una forma de definir la estructura de un objeto. Se pueden definir las propiedades y métodos que debe tener un objeto para que sea considerado de un cierto tipo.

```typescript
interface Persona {
    nombre: string;
    edad: number;
    dirección?: string;
}

let persona: Persona = {
    nombre: 'Juan',
    edad: 30,
};
```

## Tipos de datos

TypeScript soporta los mismos tipos de datos que JavaScript, como `number`, `string`, `boolean`, `null`, `undefined`, `object`, `array`, entre otros.

```typescript
let numero: number = 5;
let texto: string = 'Hola';
let booleano: boolean = true;
let nulo: null = null;
let indefinido: undefined = undefined;
let objeto: object = { nombre: 'Juan', edad: 30 };
let arreglo: number[] = [1, 2, 3];
```

## Funciones

Las funciones en TypeScript pueden tener parámetros con tipos definidos y un tipo de retorno. También se pueden definir funciones anónimas y funciones flecha.

```typescript
function sumar(a: number, b: number): number {
    return a + b;
}

let sumar2 = function(a: number, b: number): number {
    return a + b;
};

let sumar3 = (a: number, b: number): number => a + b;
```

## Tipos de unión

Los tipos de unión permiten definir una variable que puede tener más de un tipo. Por ejemplo, se puede definir una variable que puede ser un número o un string.

```typescript
let numeroOTexto: number | string = 5;
numeroOTexto = 'Hola';
```

## Tipos de intersección

Los tipos de intersección permiten combinar dos tipos en uno solo. Por ejemplo, se puede definir un tipo que tenga las propiedades de dos interfaces.

```typescript
interface A {
    a: number;
}

interface B {
    b: string;
}

let ab: A & B = { a: 5, b: 'Hola' };
```

## Tipos literales

Los tipos literales permiten definir un tipo que solo puede tener un valor específico. Por ejemplo, se puede definir una variable que solo puede tener el valor `rojo`, `verde` o `azul`.

```typescript
let color: 'rojo' | 'verde' | 'azul' = 'rojo';
```

## Tipos de tupla

Las tuplas son un tipo de datos que permite definir un arreglo con un número fijo de elementos y con tipos específicos para cada elemento.

```typescript
let tupla: [number, string] = [5, 'Hola'];
```

## Tipos de función

Los tipos de función permiten definir el tipo de una función, incluyendo los tipos de los parámetros y el tipo de retorno.

```typescript
let sumar: (a: number, b: number) => number = (a, b) => a + b;
```

## Tipos de parámetros opcionales

Los tipos de parámetros opcionales permiten definir parámetros que pueden ser omitidos al llamar a una función.

```typescript
function saludar(nombre: string, apellido?: string) {
    if (apellido) {
        console.log(`Hola ${nombre} ${apellido}`);
    } else {
        console.log(`Hola ${nombre}`);
    }
}

saludar('Juan');
saludar('Juan', 'Pérez');
```

## Tipos de parámetros por defecto

Los tipos de parámetros por defecto permiten definir un valor por defecto para un parámetro si no se le pasa un valor al llamar a una función.

```typescript
function saludar(nombre: string, apellido: string = 'Pérez') {
    console.log(`Hola ${nombre} ${apellido}`);
}

saludar('Juan');
saludar('Juan', 'Gómez');
```

## Creacion de types

Los types permiten definir un alias para un tipo de datos. Por ejemplo, se puede definir un type para un objeto con propiedades específicas.

```typescript
type Persona = {
    nombre: string;
    edad: number;
};

let persona: Persona = { nombre: 'Juan', edad: 30 };
```

## Tipos de datos no nulos

Los tipos de datos no nulos permiten definir que una variable no puede tener el valor `null` o `undefined`.

```typescript
let numero: number = 5;
let numeroNoNulo: number = 5!;
```

## Tipos de datos desconocidos

Los tipos de datos desconocidos permiten definir una variable que puede tener cualquier tipo de datos, pero no se puede acceder a sus propiedades o métodos.

```typescript
let desconocido: unknown = 5;
let numero: number = desconocido as number;
```

## as const

El operador `as const` permite definir una variable con un tipo de datos específico y que no se pueda modificar.

```typescript
let colores = ['rojo', 'verde', 'azul'] as const;
colores.push('amarillo'); // Error
```

## Genéricos

Los genéricos son una forma de definir tipos de datos que se pueden utilizar en diferentes partes del código. Por ejemplo, se puede definir una función que reciba un tipo genérico y devuelva un tipo genérico.

```typescript
function identidad<T>(arg: T): T {
    return arg;
}

let numero = identidad<number>(5);
let texto = identidad<string>('Hola');
```

## Clases

Las clases son una forma de definir objetos con un comportamiento y propiedades específicas. Se pueden definir propiedades y métodos en una clase, y luego instanciar objetos de esa clase.

```typescript
class Coche {
    marca: string;
    modelo: string;

    constructor(marca: string, modelo: string) {
        this.marca = marca;
        this.modelo = modelo;
    }

    acelerar() {
        console.log('Acelerando...');
    }
}

let coche = new Coche('Toyota', 'Corolla');
coche.acelerar();
```

## tipado en axios

```typescript
import axios from 'axios';

interface Post {
    userId: number;
    id: number;
    title: string;
    body: string;
}

axios.get<Post[]>('https://jsonplaceholder.typicode.com/posts')
    .then(response => {
        console.log(response.data);
    });
```

## tipado en fetch

```typescript
interface Post {
    userId: number;
    id: number;
    title: string;
    body: string;
}

fetch('https://jsonplaceholder.typicode.com/posts')
    .then(response => response.json())
    .then((data: Post[]) => {
        console.log(data);
    });
```

