# MagicOptimizer

## problema 
Un amigo mío juega un juego de cartas llamado Magic en formato fisico, en el formato Commander, que se juega con mazos de 100 cartas y por ser estudiante dispone de un presupuesto
limitado. Cuando quiere mejorar su mazo, tiene que lidiar con cientos de cartas candidatas cada una con sus caracteristicas coste de maná, precio, legalidad para su formato, color
de la carta y rol. y le cuesta mucho trabajo saber que conjunto de cartas realmente mejora su mazo teniendo en cuenta el presupuesto. Si elige mal, acaba gastando su dinero 
en cartas que aportan menos de lo que potencialmente podria haber conseguido con otra combinacion, o incluso acabar con un mazo peor al que tenia antes porque como el mazo tiene un 
tamaño fijo de 100 cartas meter una carta implica sacar otra y si la nueva no encaja con la curva de mana que le conviene a su mazo ha invertido dinero que no genera mejoras al mazo.


## Lógica de negocio
Para resolver este problema tenemos que partir del mazo actual, el presupuesto del que disponemos, y una lista de cartas candidatas que el jugador conoce y le interesa evaluar para su mazo.
Tanto el mazo, roles, cartas candidatas seran ingresadas a traves de un csv.Los campos de cartas del mazo y candidatas bastara con el nombre y rol, y los roles con el rol y coste de mana ideal.
El tamaño de las cartas es fijo de 100, las de las candidatas depende completamente de cuantas cartas quiera evaluar el usuario pero podriamos estimarlo a 30-40 cartas y la cantidad de roles por mazo suele promediarse entre 6-10, por tanto, no hablamos de una cantidad enorme de datos que tenga que introducir el usuario.

En este caso como se trata del formato Commander toda la estrategia se centra en un unico comandante, por tanto, el jugador tendra que definir los roles que le interesan. Tanto 
en las cartas de su mazo como en las cartas candidatas tendran que tener asignado el rol que cumplen, todo esto segun el criterio del jugador.

La curva de mana es la distribucion de coste de mana de las cartas de su mazo cada rol tendra un coste de mana ideal, definida por el usuario por que depende de su manera de jugar, para el calculo de la puntuación.

A partir de ahi hacemos lo siguiente:
1. Tendrían que pasar un filtro para descartar las cartas que no cumplen el formato seleccionado y cuyo color encaja en el mazo ademas de descartar las cartas que superan el presupuesto.
2. Calcular que roles estan cubiertos por el mazo y los que estan escasos, comparando el número de cartas que cumplen cada rol
3. Por cada candidata se calcula una puntuación, que pondera mas cubrir un rol escaso y que la carta encaje bien en la curva de maná segun su coste.
4. Una vez obtenido todas las cartas filtradas y puntuadas, calculamos el subconjunto que maximiza la suma de puntos sin superar el presupuesto.

La puntuacion de las cartas se obtendria con el producto Punt=Prol*Coste.
Prol=1/(1+{numero de cartas que ya cubren el rol}), este nunca llega a valer 0 y si el rol no ha sido aun cubierto vale 1.
Coste=1/(1+|{costecartai-costeidealrol}|) este tampoco llega a valer nunca 0 y cuando te alejas decae el valor alejandose de 1. 
## Necesidad de acceso a la nube
Haría falta desplegar el servicio en la nube porque a diario se actualiza los precios de las cartas y conviene almacenarlos para no tener que consultarlos cada vez que se hace
el calculo.

Otro motivo por el que haria falta el servicio en la nube es por que datos como la lista de candidatas se va actualizando, cuando, por ejemplo, mi amigo descubre cartas
nuevas o cuando compra una carta nueva para el mazo y tiene que actualizarlo. Así si lo edita desde el móvil luego podra verlo desde el ordenador y viceversa.

Por ultimo, el procesamiento es pesado para hacerlo cada vez en el móvil asi que lo mejor seria que lo haga un servicio centralizado y con el movil solo se consulte los resultados ya calculados.
## Juego de Rol
![Fotografía de la tarjeta del cliente](img/tarjeta_cliente.png)
![Fotografía de la tarjeta del desarrollador](img/tarjeta_desarrollador.png)
 
## Datos
[obtención de los datos](Datos/datos.md)
 
## Documentación

[Configuración del repositorio](docs/configuracion.md)
