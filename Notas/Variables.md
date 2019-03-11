# Variables: Generalidades

En Julia, una variable es un nombre asociado (o ligado a un valor). 
```julia
# Asigna el valor 10 a la variable x
julia> x = 10
10

# Existen otros tipos de valores que se pueden asignar, como las cadenas (strings)
julia> x = "Hello World!"
"Hello World!"

#Cualquier caracter UNICODE es válido
julia> UniversalDeclarationOfHumanRightsStart = "人人生而自由，在尊严和权利上一律平等。"
"人人生而自由，在尊严和权利上一律平等。"

julia> δ = 0.00001
1.0e-5
```
Es muy fácil reasignar valores a las variables, incluso variables y funciones preasignadas.
```julia
# Reassign x's value
julia> x = 1 + 1
2
julia> pi = 3
3

julia> sqrt = 4
4
```
Sin embargo, si defines funciones o valores que ya están en uso tendrás problemas.
```julia
julia> pi
π = 3.1415926535897...

julia> pi = 3
ERROR: cannot assign variable MathConstants.pi from module Main

julia> sqrt(100)
10.0

julia> sqrt = 4
ERROR: cannot assign variable Base.sqrt from module Main
```
## Nombrando variables
Julia permite que los nombres de variables sean del tamaño que uno quiera, no hay una limitante de espacio, y se pueden incluir números, guiones bajos y caracteres Unicode. No hay excusa para no **usar variables descriptivas**.

En un script formal evita en mayor medida usar las variables de una sola letra (a, s, etc,) a menos de que sea para un ejemplo bobo en donde estemos probando algo (a = 2 ; b = im ; a + b).

En lugar de `a = [sin(x) for x in [0:0.1:2pi]]`, vamos a utilizar un nombre descriptivo como senos, lista_sin o cualquier cosa que me diga lo que contiene el arreglo.

Si definimos una función que se repite N veces, no vamos a usar una variable N, vamos a preferir num_iters, iters, reps, etc.

Cómo esta es una clase de física, vamos a utilizar muchas letras griegas. Cuando quede claro del contexto lo que significa la variable $\theta$ (por ejemplo es el ángulo del tiro parabólico), en lugar de utilizar la variable theta vamos a aprovechar el soporte Unicode de Julia y escribir \theta y luego <TAB> para que la variable sea una letra griega de verdad.

## Nombres prohibidos
```julia
julia> 76trombones = "gran calenda"
ERROR: syntax: "76" is not a valid function argument name
julia> more@ = 1000000
ERROR: syntax: extra token "@" after end of expression
julia> struct = "Advanced Theoretical Zymurgy"
ERROR: syntax: unexpected "="
```

##Opcional
Las convenciones que se consideran "de buena educación" en Julia pero no vas a perder puntos por no seguirlas.

En el manual de Julia puedes leer que se acostumbra:

* Que los nombres de variables sean en minúscula, y que se haga la separación de palabras con un guión bajo. Se recomienda no abusar de los guiones.
* Los nombres de las funciones sean en minúsculas. Idealmente se tiene que evitar que tengan muchas palabras distintas.
* Las funciones que modifican a sus argumentos lleven un signo de exclamación ! al final del nombre (ejemplo: push!).
