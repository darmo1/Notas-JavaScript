👨‍🏫 Notas de JavaScript 👨‍🚀 👩‍🚀

🚀🚀 Estos son apuntes de consulta personal de cursos de JavaScript 🚀🚀
Sientete libre de consultar las notas si te son de utilidad.
Feel free of usign if these notes are useful to you

## Prototype: 😎
### te permite atar una propiedad a un objeto 
>> Sentencia :    objeto.prototype.nombrePropiedad = el valor a contener

function mostrarInformacionTarea( tarea, prioridad ){
    return `La tarea ${tarea} tiene una prioridad de ${prioridad}`;
}


const mostarInfo = mostrarInformacionTarea('Aprender Js y React', 'Urgente')
console.log(mostrarInfo)


function Tarea( nombre, urgencia){
    this.nombre = nombre
    this.urgencia = urgencia
}

Tarea.prototype.mostrar = function mostrarInformacion(){
     return `La tarea ${this.nombre} tiene una prioridad de ${this.urgencia}`;
}
const tarea1 = new Tarea('Aprender JavaScript y React', 'Urgente');
console.log( tarea1.mostrarInformacionTarea() );

# Destructuring 😍 
>Se encarga de extrar valores y crean variables con esa determinada referencia de objeto o posicion de array

const aprendiendoJS= {
    version: 'ES6+',
    frameworks : ['React', 'vueJS', 'AngularJs']
}

let version = aprendiendoJS.version.nueva;
let framework = aprendiendoJS.frameworks[0];

The destructuring is a way to create a variable refering to a specific object, so:

let { version, frameworks} = aprendiendoJS;
console.log(version)
console.log(frameworks)

# Object literal enhancement 🤓

const band = 'metalica'
const genero = 'Heavy Metal'
const canciones = ['Master of puppets', 'Seek & Destroy', 'Enter Sandman'];

const metallica = { banda, genero, canciones}
esta es la nueva forma, y en un antiguo codigo seria
const metallica = {
    banda: banda,
    genero: genero,
    canciones: canciones
}

Particularidad con las funciones dentro de objetos

const obj = {
    name: 'Danilo',
    age: 26,
    showInfo: function(){
        `This is my name: ${this.name} and I'm ${this.age} years old`
    }
}

when you want to transform the obj to Object literal enhacement  you could be to write something like that 
const obj = {
    name: 'Danilo',
    age: 26,
    showInfo(){
        `This is my name: ${this.name} and I'm ${this.age} years old`
    }
}

## Array : 🤗

const carrito = ['Producto 1','Producto 2','Producto 3']
Existen varias funciones o métodos para operar 

>ForEach
carrito.forEach( el => html += <li> el </li>)

>Map  
carrito.map(el=>{
    return 'El producto es ' + el
})

>Filter
const personas = [
    {nombre: 'Juan', edad:23, aprendiendo:'JavaScript'},
    {nombre: 'Pablo', edad:23, aprendiendo:'PHP'},
    {nombre: 'Alejandra', edad:23, aprendiendo:'AdobeXD'},
    {nombre: 'Karen, edad:23, aprendiendo:'Python'},
    {nombre: 'Miguel, edad:23, aprendiendo:'ReactJS'},
    ]

*Debe retornar y catch el resultado en una variable* 
[TRAE TODOS LOS VALORES EN UN ARRAY QUE CUMPLAN LA SENTENCIA DEL RETURN]
    const mayores = personas.filter( persona => {
       return persona.edad > "20"
    })

    console.log(aprendiendo)
>Find

[TRAE EL PRIMER VALOR EN UN ARRAY QUE CUMPLAN LA SENTENCIA DEL RETURN]
    const e = personas.find( persona => {
       return persona.aprendiendo == "JavaScript"
    })

>Reduce

Puedes crear una operacion con este método 
    const total = personas.reduce( edadTotal, persona => {
       return edadTotal + persona.edad;
    })

# Object Keys 🤭

const obj = {
    name: 'Danilo',
    age: 26,
    profession: 'Web Developer'
}

Object.keys(obj) Esto se traera un array con todos las keywords del objeto! 
Object.value(obj) Esto se traerá un array con todos los valores del objeto literal

# Spread Operator 🤩

let lenguajes = ['JavaScript', 'PHP', 'Python']
let [ultimo] = lenguajes.reverse(); Traerá python, pero un efecto colateral es que el array quedará al revés
['Python', 'PHP', 'JavaScript']
 tendriamos que volver a generar el .reverse del array
 por eso es importante el spreadOperator

let [ultimo] = [...lenguajes.reverse()];

let frameworks = ['ReactJS', 'Laravel', 'Django']

let combinacion = [...lenguajes, ...frameworks] // Aqui lo que hacemos es copiar los valores de cada posicion del index de los arrays 

## Promises 😋

const aplicarDescuento = new Promise((resolve, reject) => {
    setTimeOUT(()=>{
        let descuento = false;

        if(descuento){
            resolve('Descuento Aplicado')
        }
        else{
            reject('No se pudo aplicar el descuento')
        }
    }, 3000)
})

Pending State is called too  .then

aplicarDescuento.then(resultado => {
    console.log(resultado)
}).catch(error => console.log(error))

## Promises con AJAX 🙌

const descargarUsuarios = cantidad => new Promise((resolve, reject)=> {
    const api= `URL/api/?result=${cantidad}&nat=us`;

    //Llamado a ajax
    const xhr = new XMLHttpRequest();
    //Abrir conexion
    xhr.open('GET', api, true);

    //On load
    xhr.onload = ()=>{
        if(xhr.status == 200){
            resolve(JSON.parse(xhr.responseText).results);   //Este TRANSFORMA el json a un objeto de javascript
        }else{
            reject(Error(xhr.statusText));
        }
    }
    //Optional
    xhr.onerror = error=> reject(error)

    //Send
    xhr.send()
})

descargarUsuario(20).then(
    miembros => console.log(miembros),
    error => console.error( new Error('Hubo un error' + error))
)

## Programacion Orientada a Objeto ✍️

// Escribir classes

class Tarea{
    constructor(nombre, prioridad){
        this.nombre = nombre;
        this.prioridad = prioridad
    }
    mostrar(){
        return `This is my name: ${this.nombre} and I have a priority ${this.prioridad}`)
    }
}

>Crear Objetos
let tarea1 = new Tarea('Aprender JavaScript','Alta');
let tarea2 = new Tarea('Preparar Café','Media');
console.log(tarea2.mostrar())

>Herencia
*La ventaja de la herencia es que puedes acceder a todos los métodos que estas heredando del objeto padre... o puedes reescribir el método en caso de que quieras modificar la funcion original.*  

class ComprarPendientes extends Tarea {
    constructor(nombre, prioridad, cantidad){
        super(nombre, prioridad);
        this.cantidad = cantidad;
    }
}

let compra1 = new CompraPendientes('Shampoo', 'Alta', '10')


## Módulos en javaScript  🥳

export const nombre de la variable
import { nombre de la variable} from "root path"

cuando es export default a la hora de importan se eliminar los curly brackets { } solo se declara la variable y la ruta
en html cuando se agrega el <script></script> debemos declarar un atriburo de type="module" <script src="" type="module"></script>

## Exportando funciones 😊

export const crearTarea = ()=>{
    return 'I am exporting a function 
}
import {nameFunction}

const tarea1 = crearTarea()
console.log(tarea1)

## Exportando Clases 🤩

export default class Tarea{
    constructor(nombre, prioridad){
        this.nombre = nombre;
        this.prioridad = prioridad
    }
    mostrar(){
        return `This is my name: ${this.nombre} and I have a priority ${this.prioridad}`)
    }
}

import Tarea from 'ruta donde está el pedazo de código'

