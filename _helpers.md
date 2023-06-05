# Helpers

Las funciones de apoyo (Helper function) son usadas para la reusabilidad del código en cuenstion.

Dentro de un helper se colocan funciones que se relacionen en su finalidad de uso.

  De esta forma son llamadas todas desde un solo archivo JS para reducir las líneas de código en caso de necesitar trabajar con la misma funcion en diferentes archivos JS.

~~~javascript

------------------------------------
//helper.js
  export const plus = (x,y) => {
    return x + y
  }

  export const minus = (x,y) => {
    return x - y
  }
------------------------------------

----------------------------------------------- 
// app.js
  import { plus, minus } from './helper.js'

  plus(5,10)

  minus(7,4)
-----------------------------------------------
~~~