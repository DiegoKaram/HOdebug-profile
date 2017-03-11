#Respuestas

##Varios Bugs
Al compilar y correr el debugger sin ninguna flag (aparte de `-o`) ocurre que
dbg no puede encontrar simbolos de debugg, además, como el programa fue
optimizado, los nombres de las variables cambiaron y no se los encuentra fácil.
  Cuando compilamos usando el flag `-g`, los datos necesarios para debuggear
son pasados a gdb.
  Si  usamos `-Wall` y `-O0`, conseguimos que el compilador arroje unos warnings
que nos llaman la atención a posibles problemas , como el hecho de que algunos
punteros no están inicializados, y, al no estar optimizado el código, podemos
manejar las variables (y la estructura en general) del programa con facilidad
en gdb.

##FPE
La funcion `square_root` tiene indefinida la función `sqrt()`. Para que compile,
podemos usar el flag `-lm`.
  Usando estas funciones sin linkearlas con los archivos en `fpe/` obtenemos
resultados normales, excepto si intentams dividir por cero, o por `inf`, en esos
casos se llevan a cabo las operaciones pero los resultados son "extraños".
  Parece que al agregar la trap `-DTRAPFPE` a la compilación se incluyen los
"errores" que saltan al intentar hacer una opercaión de punto flotante inválida
(como dividir por cero) y ahora los programas no arrojan resultados, sólo el
mensaje `Excepción de coma flotante` (core' generado).

##Segmentation Fault
 fasf.

##funny
Si se compila el codigo sin el flag se obtiene un segmentation fault al correr
el ejecutable. Si se usa `-DDEBUG` se imprime una frase y despues hay
segmentation fault.
