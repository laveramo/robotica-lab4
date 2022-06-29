# Laboratorio 4 Robótica: Robótica Industrial
# Introducción
El objetivo de este laboratorio consistía en realizar las iniciales de los integrantes del equipo (J, L) en una superficie plana y replicar esta escritura en un plano inclinado 30° y además con una ubicación distinta. Para esto, se diseñó una herramienta (porta-marcador) que correspondiera al robot ABB IRB140 y que tuviera en cuenta algunos requerimientos de diseño. Posteriormente se desarrolló un módulo de RAPID en el software Robotstudio que permitió simular las trayectorias a realizar por el robot para la escritura y finalmente, después de comprobar por simulación un correcto procedimiento se llevó este módulo un robot IRB140 real.

## Diseño de la herramienta
Para diseñar el porta-marcador se tuvo en cuenta que la superficie en dónde se escribirían las letras no era totalmente plana, por el contrario, tenía un desnivel. Por esto, se hacía necesario en alguna parte de la herramienta implementar un resorte que permitiera un movimiento amortiguado del marcador para no dañarlo. Por sencillez, se optó por usar un tubo de PVC con dos tapas: una superior totalmente cerrada y una inferior con hueco para permitir el paso de la punta del marcador. Adicional a esto, se imprimió la pieza cilíndrica que permitía la únión de este tubo con el flange del robot.

## Código en RAPID
El archivo *ModuleJL.mod* es el módulo de RAPID usado para realizar la trayectoria del robot que permitía escribir las letras J y L. En la parte inicial del código se encuentra definida la herramienta m100 que fue calibrada anteriormente, los workobjects o sistemas de referencia `workobject` y `prueba1` y además, los puntos que se usarían para construir las tracyectorias de las letras (Home, J_1, J_2, ... , J_7, L_0, L_1, ... ,L_4).

Posteriormente, dentro del main se ejecutan 2 procesos llamados J y L, los cuales representan las instrucciones necesarias para realizar cada una de estas letras. El proceso llamado J contiene inicialmente una instrucción `MoveJ` hacia Home, luego una instrucción de este mismo tipo hacia el punto J_1, el cual es una de las esquinas de la letra J. A continuación se usan tanto instrucciones `MoveL` y `MoveC` para realizar esta letra y cuando termina, se traslada a un punto que está unos centímetros por encima del punto final, de esta forma, se podrá mover la herramienta al punto donde inicia la letra L. 

El proceso L, es similar al anterior, en este caso sólo se usan instrucciones `MoveL` debido a que no se necesita realizar curvas. Se repite el proceso de llevar la herramienta a un punto superior del punto final antes de llevarlo a Home, esto con la finalidad de no tener una pequeña marca antes de que se regrese a Home.
## Simulación en Robotstudio e implementación con robot real
# Conclusiones
