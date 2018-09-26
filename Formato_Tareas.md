## Formato de Tareas

Las tareas se entregan vía email en mi correo, `mario.villasate@ciencias.unam.mx`.

Las tareas se deberán entregar en archivos de Jupyter (\*.ipynb) nombrados propiamente. Favor de enviar un sólo notebook llamado 
`tarea$N_$Nombre_$Apellido.ipynb`; esto hará más fácil organizar mis archivos. Ejemplo: `tarea10_Mario_Villasante.ipynb`.

Les pido entreguen sus tareas en Jupyter, ya que es una herramienta muy sencilla en la cual van a poder explicar sus códigos intercalando 
celdas tipo *markdown* con celdas de código. No olvide comentar su código, para hacerlo legible. Si necesitas usar **ecuaciones escríbelas con LaTeX**.

El notebook debe ser ejecutable, es decir, cada celda debe correr sin errores, y debe reproducir la salida que aparece en la pantalla.

## Ojo

Al programar la respuesta no es única, y no lo es tanto por el algoritmo uno puede utilizar como por el estilo que uno le da a su código.

Respecto a lo primero, (casi) todas las respuestas son válidas, si el código funciona funciona. Respecto a lo segundo, vamos a tener que seguir algunas convenciones.

## Espacio
El código se debe de ver limpio, y para ésto es indispensable utilizar espacios y líneas en blanco. (Sin contar la indentación. No hay excusa para que no sea perfecta porque el editor del notebook la maneja automáticamente.)

En lugar de `a=3`, es mejor `a = 3`. En lugar de `raiz(algo,otra,cosa)` vamos a poner espacios después de cada coma: `raiz(algo, otra, cosa)`.

Y en los bloques de código, vamos separar diferentes pasos o ideas con líneas en blanco.

## Variables
Julia permite que los nombres de variables sean del tamaño que uno quiera, no hay una limitante de espacio, y se pueden incluir números, guiones bajos y caracteres Unicode. Por esta razón, **no hay excusa para que las variables no sean descriptivas**.

En lugar de `a = [sin(x) for x in [0:0.1:2pi]]`, vamos a utilizar un nombre descriptivo como `senos`, `lista_sin` o cualquier cosa que me diga lo que contiene el arreglo.

Si definimos una función que se repite N veces, no vamos a usar una variable N, vamos a preferir `num_iters`, `iters`, `reps`, etc.

Cómo esta es una clase de física, vamos a utilizar muchas letras griegas. Cuando quede claro del contexto lo que significa la variable &theta; (por ejemplo es el ángulo del tiro parabólico), en lugar de utilizar la variable theta vamos a aprovechar el soporte Unicode de Julia y escribir `\theta` y luego `<TAB>` para que la variable sea una letra griega de verdad.

## Funciones
Las funciones deben tener un nombre más o menos representativo de lo que se supone que hacen, de preferencia de manera resumida, sin que deje de ser legible. `mi_raiz` es un buen nombre, `rzcd` no lo es porque es difícil entender que está abreviando raiz cuadrada.

Los argumentos de las funciones definen variables, y todo lo que se dijo en el párrafo anterior aplica aquí. En lugar de `mi_función(x,n)` voy a preferir `mi_funcion(arreglo, num_iters)`.

Dentro de las funciones es común que utilice variables que sólo viven por un momento, que me sirven para almacenar algo temporalmente. En lugar de llamarlas `a`, por qué no nombrarlas `tmp` o algo del estilo. Sí construyo una variable que al final va a contener el cálculo que quiero regresar, puedo llamarla `out`. Y si utilizo una variable que funciona como contador, voy a llamarla  `contador` o `cont`, por ningún motivo `n`.

Ejemplo:
```julia
mi_funcion_copia(arreglo, len_arreglo)
    # Una función que hace una copia del arreglo que le doy como argumento

    # Creamos un arreglo vacío que contendrá la salida
    out = Vector(Int, len_arreglo)

    for i in 1:len_arreglo
        out[i] = arreglo[i]
    end

    out
end
```
Llamados a las funciones
Muy seguido vamos a utilizar una función montones de veces, llamándola con diferentes argumentos para ver cómo se comporta un sistema físico. Por ejemplo, en el problema del tiro parabólico nos va a interesar llamar a la función que calcula la trayectoria con diferentes velocidades iniciales y ángulos.

Cuando lo hagamos, no vamos a hacer ésto:
```julia
tiempos = linspace(0, 10, 256)

trayectoria(tiempos, 10, pi/2)
```
Lo correcto es siempre hacer es lo siguiente:
```julia
tiempos = linspace(0, 10, 256)
v_0 = 10
θ = pi/2

trayectoria(tiempos, v_0, θ)
```

La diferencia entre las dos versiones es que ahora el ayudante sabe qué es lo representan el 10 y el pi/2.

Mejor aún es poner
```julia
t_inicial = 0.0
t_final = 10.0
num_pasos = 256

tiempos = linspace(t_inicial, t_final, num_pasos)
v_0 = 10
θ = pi/2

trayectoria(tiempos, v_0, θ)
```
Es decir, seguimos la siguiente regla: cada numéro que aparece debe tener un nombre.

## Opcional: convenciones de Julia
Hasta aquí las indicaciones eran obligatorias. Lo que sigue es opcional; son las convenciones que se consideran "de buena educación" en Julia pero no vas a perder puntos por no seguirlas.

En el manual de Julia puedes leer que se acostumbra:

- Que los nombres de variables sean en minúscula, y que se haga la separación de palabras con un guión bajo. Se recomienda no abusar de los guiones.
- Que los nombres de las funciones sean en minúsculas. Idealmente se tiene que evitar que tengan muchas palabras distintas.
- Que las funciones que modifican a sus argumentos lleven un signo de exclamación ! al final del nombre (ejemplo: push!).
