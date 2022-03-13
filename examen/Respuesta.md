orden de impresion en pantalla:

new promise
async function
nextTick1
nextTick2
nextTick3
then1
then2
microTask1
microtask2
immediate1
immediate2
timeout1
timeout2

test 1

el codigo comienza con el objeto promesa y alli se ejecuta el primer log, en ese mismo log resuelve la promesa, tambien se declara un then() el cual se ejecutara cuando termine la fase. Se definie tambien un foo, este foo llama al segundo log, se debe saber que las funciones asincronicas retornan una promesa  asi que se define un .then. al final de esta primera fase, todas las tareas se pondran en un orden donde las macrotareas (setImmediate y el setTimeout) estaran en la macroQueue y las micro tareas (process.NextTick, las promesas resueltas y queuemicrotask) estaran en la microQueue. En esta siguiente fase el setImmediate ejecuta las micro tareas (se prioriza el process.NextTick), despues de eso, se ejecutan las promesas (las dos que se declararon), pero antes de ejecutar, se muestra el tercer, cuarto y quinto log. esta ejecucion mostrarara el sexto y septimo log, al final se mostraran las microtareas, seguidamente se muestra el octavo y noveno log, el deciomo y decimo primer se muestra cuando se ejecuta el setImmediate, se toma en cuenta que siguiente fase verifica que ninguna microtarea quede en la cola. para demiostrar el decimo segundo y tercer log, se que los dos setTimeout han sido retirados, finalizando asi el codigo.

new promise
async function
nextTick 1
nextTick 2
nextTick 3
then 1
then 2
microtask 1
microtask 2
immediate 1
immediate 2
timeout 1
timeout 2

test 2

este codigo se comporta de una manera partiular, se parece al test 1, lo unico diferente es este const, que se va ejecutando, pero va realizando otras tareas, y cuando termine de ejecutar la const, llamara la delcaracion readFile y ejecutara todo el codigo.

new promise
async function
then 1
then 2
microtask 1
microtask 2
nextTick 1
nextTick 2
nextTick 3
immediate 1
immediate 2
timeout 1
timeout 2

test 3

esta linea de codigo es la misma que el test 2, la unica diferencia es que es un archivo ".mjs" (ECMAScript) el cual necitariamos exportar para su funcionamiento