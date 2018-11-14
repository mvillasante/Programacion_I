# Sintaxis y comportamiento básico en la REPL

Una de las mejores maneras para familiarizarse con *Julia* y su sintaxis es usando la REPL.
Aunque no se recomienda para desarrollar código, sí puede ayudarnos a buscar documentación y para probar pequeñas secciones de nuestros códigos.

## Ayuda y buscando documentación
Si escribes **?** al inicio de cada línea 
```julia
julia> ?
```
cambiarás al modo de ayuda (el prompt cambia de color):

```julia
help?>
```
Podrás escribir el nombre de cualquier objeto o función (sin paréntesis) y obtener información:
```julia
help?> exit
search: exit atexit textwidth process_exited method_exists indexin nextind IndexLinear TextDisplay istextmime
   
exit(code=0)
   
Stop the program with an exit code. The default exit code is zero, indicating that the 
program completed successfully. In an interactive session, exit() can be called with the 
keyboard shortcut ^D.
   
julia>
```
*Nota que en la primera linea se muestran todas las funciones y objetos con el bloque de caractéres "exit" en su nombre*

Si quieres buscar dentro de la documentación, no sobre el índice de objetos en julia, puedes usar **apropos()**  y buscar una cadena de caractéres:
```julia
julia> apropos("determinant")
LinearAlgebra.det
LinearAlgebra.logabsdet
LinearAlgebra.logdet
```
## Modo Shell
Si necesitas ejecutar comandos de shell (la terminal del S.O.) puedes usar un punto y coma:
```julia
julia > ?
```
y cambiarás automáticamente al modo shell desde el cual podrás ejecutar cualquier comando propio de la terminal de tu S.O.:
```shell
shell> ls 
file.txt executable.exe directory

julia>
```
## Autocompletar: Tecla `<TAB>`
La tecla `<TAB>` ayuda a completar, o muestra una lista de sugerencias, de lo que acabas de escribir. Por ejemplo, si escribo `w` y después presiono la tecla TAB
(debes presionar dos veces si existen más de una opción), se muestra una lista con todas las funciones disponibles que comienzan con la letra "w":
```julia
julia> w <TAB>
wait    walkdir  which    while    widemul  widen    withenv  write
```
## Historial
La REPL hace un historial de todos los comandos que tecleas, puedes usar las flechas Arriba o Abajo para buscar, de esta manera puedes ahorrarte la molestia de volver a teclear una expresión
con múltiples líneas. Si has tecleado muchos comandos, puedes buscar comandos al presionar `Ctrl+R` o `Ctrl+S`. 

## Carácteres Unicode 
Una de las características más divertidas de Julia es que puedes usar cualquier caractér UNICODE para asignar variables. La lista incluye el alfabeto griego,
subscripts, símbolos matemáticos especiales y *emojis* \:astonished: \:smirk: \:smiley:. Por ejemplo:
1. `julia> \sqrt <TAB>` -> `julia> √`
2. `julia> \alpha <TAB>` -> `julia> α`
3. `julia> \in <TAB>` -> `julia> ∈`
4.  `julia> \:wolf: <TAB>` -> `julia> `\:wolf:

Una lista completa de los caractéres que puedes usar la puedes encontrar en https://docs.julialang.org/en/latest/manual/unicode-input/#Unicode-Input-1

## Rendimiento y tips
Una práctica que debes tener en claro, no solamente cuando trabajes en la REPL, es modular el código. Cuando escribas código debes
introducir el código dentro de funciones y organizarla dentro de módulos y paquetes. Esto se debe a la manera de trabajar del compilador
de Julia, si organizas de esta manera tu código el compilador trabajará más rápido.

Definir variables globales es una de las prácticas más comunes en otros lenguajes de programación, esto lo deberás evitar siempre que puedas.

Más tips sobre rendimiento los puedes encontrar en el manual de Julia https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-tips-1
