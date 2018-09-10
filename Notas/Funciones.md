## Funciones

Una *función* es un bloque de declaraciones con un nombre. A diferencia con las funciones matemáticas, las funciones en Julia aceptan cero o más argumentos y regresan cero o más respuestas.

Las funciones se pueden definir de dos maneras:

#### Implícitas
```julia
julia> f(x) = x * x
f (generic function with 1 method)

```
#### Explícitas
```Julia
function nombrefunc(arg1, arg2)
   expression
   expression
   expression
   ...
   expression
end

```
#### Regresando más de un valor
```julia
function foo(a,b)
  a+b, a*b
end
```
#### Orden de ejecución
En el REPL puede ser confuso el orden de ejecución, evalua todo cada vez que hacemos una declaración. Un script puede ser más claro; el orden de ejecución empieza con la primera línea y ejecuta cada declaración en orden descendente, excepto cuando se encuentra con una función.

Al definir una función, no se cambia el orden de ejecución de Julia, pero las declaraciones dentro de la función no se evalua hasta que se llama a la función.

Es imperativo definir las opciones antes de usarlas.

#### Variables opcionales
Podemos usar funciones con parámetros definidos los cuales se pueden cambiar
```julia
function f(a1, opta2=2)#; key="foo")
   println("argumento obligatorio: $a1")
   println("argumento opcional: $opta2")
   #println("keyword argument: $key")
end
f (generic function with 2 methods)
```

#### Cualquier número de argumentos

```julia
function fvar(args...)
    println("introduciste $(length(args)) argumentos")
    for arg in args
       println(" argumento", arg)
    end
end
```

#### Variables locales
Debemos tener claro que las variables que se definen dentro de una función desaparecen una vez que la función termina de ejecutarse

```julia
function set_to_5(x)
    x = 5
end
```
```julia
julia> x = 3
3

julia> set_to_5(x)
5

julia> x
3
```

#### Return o no Return
Las funciones regresan el valor de la última expresión calculada.
```julia
function noreturn(x)
  println(x)
  return string("este es regreso $x")
  println(x^5)
  x^2
end
```
Nótese que las declaraciones abajo de la línea de `return` ni siquiera son evaluadas.

#### Función de funciones
```julia
function create_exponent_function(x)
    newfunction = function (y) return y^x end
    return newfunction
end
```
#### Especificando tipos de argumento
```julia
function check_longitude_1(loc)
    if -180 < loc < 180
        println("longitude $loc is a valid longitude")
    else
        println("longitude $loc should be between -180 and 180 degrees")
    end
end
 check_longitude_1 (generic function with 1 method)

 function check_longitude(loc::Real)
    if -180 < loc < 180
        println("longitude $loc is a valid longitude")
    else
        println("longitude $loc should be between -180 and 180 degrees")
    end
end

 ```

 #### Aprovechando los tipos de parámetros

 ```julia
 julia>function test(a::T) where T <: Real
    println("$a is a $T")
end
test (generic function with 1 methods)
```



```julia
function findodds(a::Array{Int64,1})
   findall(isodd, a)
end
```
### ¿Por qué y para qué las funciones?
* Al crear una función se nombra un conjunto de declaraciones, lo cual hace mas fácil leer el código y corregirlo
* Las funciones pueden hacer un programa más corto al evitar código repetitivo
* Al dividir el código en funciones es más sencillo corregir una sección a la vez y después ensamblar las partes para crear un programa más complejo.
