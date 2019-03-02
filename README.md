# Cotxox

## Exam Training 2

Este es el examen de programación de Dual de febrero del año 2017. 
Practica con él porque la metodología será la misma este año. 

Vamos a construir un prototipo de la aplicación Cotxox
que permite gestionar el traslado de turistas desde el aeropuerto
a determinadas zonas de la isla de Mallorca, y provoca huelgas
de taxistas a discreción.

### Prepara el proyecto

1. Crea un nuevo proyecto en tu cuenta en Github.

2. Crea un nuevo directorio en tu equipo y clona el repositorio de Github.

3. Crea un proyecto Maven.

4. Copia y pega la función principal Cotxox.java. Utilízala como guía en el proceso TDD. No puedes modificar su código.

5. Completa las clases que necesites implementando los casos test que necesites.

6. Organiza las clases en sus paquetes correpondientes. 

   Observa el esquema propuesto en el import de la clase principal Cotxox.java: 

    + import org.foobarspam.cotxox.carrera.Carrera;
    + import org.foobarspam.cotxox.conductores.Conductor;
    + import org.foobarspam.cotxox.conductores.PoolConductores;
    + import org.foobarspam.cotxox.tarifa.Tarifa;
    + import org.foorbarspam.cotxox.main.Cotxox;

### Cómo entregar el código

Realiza commits periódicamente mientras avanzas en el desarrollo de la aplicación.

Publica el proyecto en tu GitHub.

Además, exporta el proyecto desde Eclipse o Netbeans. 
O accede a la carpeta del proyecto en VSCode, comprímela en un zip y envíame el archivo por correo electrónico.

### Salida de la aplicación

Intenta que la salida del programa sea lo más parecida posible a la imagen que se proporciona en el fichero "Salida consola cotxox.png".

### Historias de usuario

Crea un documento donde escribas las historias de usuario correspondientes a los 5 hitos del proceso, representados por estas las 5 imágenes proporcionadas.

### Diagrama de clases UML

Realiza un pequeño diagrama de clases UML que muestre la relación entre las clases que has construido, con su interfaz pública y privada.

### Código

#### Clase Carrera

##### Atributos

* crea las variables de instancia que estimes oportunas.

* tiempoEsperado del trayecto

* tiempoCarrera tiempo real empleado en el trayecto

* costeTotal real del trayecto

* conductor asignado a la carrera

##### Métodos

* getTarjetaCredito() devuelve el número de la tarjeta de crédito del usuario/a.

* getOrigen() devuelve el lugar de origen del trayecto.

* getDestino() devuelve el lugar de destino del trayecto.

* getDistancia() devuelve la distancia entre el origen y el destino.

* getCosteEsperado() devuelve el coste esperado del trayecto, cuyo cálculo es responsabilidad de la clase Tarifa.

* asignarConductor(PoolConductores conductores) recibe la flota de conductores y asigna un conductor a la carrera. Le pide a la clase PoolConductores que le asigne un conductor.

* getCosteEsperado() le pregunta a la clase Tarifa cuál es el coste total esperado.

* realizarPago(pago) recibe el pago y lo almacena en el atributo costeTotal

* recibirPropina(propina) recibe la propina que paga el usuario

* liberarConductor() establece que el conductor asignado a la carrera queda libre tras el servicio.

#### Clase Tarifa

##### Atributos

* costeMilla Cotxox fija en 1.35€ el coste de la milla.

* costeMinuto Cotxox fija en 0.35€ el coste del minuto.

* costeMinimo El coste mínimo que cobra Cotxox por un viaje es de 5€.

* porcentajeComision la comisión que cobra cotxox sobre el coste del viaje es del 20%.

##### Métodos

* getCosteDistancia(distancia) devuelve la parte del coste del trayecto debido al a distancia.

* getCosteTiempo(minutos) devuelve la parte del coste del trayecto debido a su duración en minutos.

* getCosteTotalEsperado(carrera) devuelve el coste total esperado de la carrera que recibe en función de la distancia esperada
y el tiempo esperado. El coste total esperado no puede ser inferior al mínimo.

#### Clase Conductor

##### Atributos

* nombre del conductor

* modelo modelo del coche

* matricula

* valoracionMedia valoración media del conductor

* valoraciones array de longitud variable que almacena todas las valoraciones del conductor

* ocupado indica si el conductor está prestando un servicio o está libre.

##### Métodos

* setValoracion(valoracion) añade la nueva valoración y actualiza la valoración media del conductor.

#### Clase PoolConductores

##### Atributos

* poolConductores es un array de longitud variable de conductores

##### Métodos

* El constructor PoolConductores(conductores) recibe un array de longitud variable de conductores.

* asignarConductor()selecciona un conductor libre entre la flota y lo devuelve, estableciendo que ese conductor está ahora ocupado.