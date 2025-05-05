### Energía Potencial y Energía Cinética

Donde:
- **Vg** es la energía potencial debido a la gravedad.
- **Vs** es la energía potencial debida a los resortes.
- **Kh** es la energía cinética del hub.
- **Kl** es la energía cinética de la carga.
- **m** es la masa del eje.
- **g** es la constante de gravedad.
- **h** es la altura del centro de gravedad del enlace con respecto a la posición de reposo.
- **Jh** es la inercia en la salida del motor.
- **Jl** es la inercia del brazo.
- **Ks** es la rigidez del resorte.

El valor de la constante **Ks** depende de la forma en que los resortes están conectados al enlace. Según el manual de Quanser, la expresión para **Ks** es:

\[
K_s = \frac{2R}{D} \left( \frac{3}{2} \left( Dd - Rr \right)^{\frac{2}{3}} \right) Fr + \left( Dd - DLd + Rr \right)^{\frac{2}{3}} L
\]

Donde:
- **R** es el punto de anclaje del brazo.
- **d** es el punto de anclaje del cuerpo "Y".
- **r** es el punto de anclaje del cuerpo "X".
- **K** es la rigidez del resorte.
- **Fr** es la fuerza restauradora del resorte.
- **L** es la longitud del resorte en reposo.
- **D** es el valor constante del resorte (según el manual de Quanser).

### Lagrangiana y Ecuaciones de Movimiento

La Lagrangiana está dada por:

\[
L = K - V
\]

Las ecuaciones de movimiento de Lagrange se expresan como:

\[
\frac{d}{dt} \left( \frac{\partial L}{\partial \dot{\beta}} \right) - \frac{\partial L}{\partial \beta} = 0
\]

\[
\frac{d}{dt} \left( \frac{\partial L}{\partial \dot{\theta}} \right) - \frac{\partial L}{\partial \theta} = \tau
\]

Donde \( \tau \) es el par de torsión producido por el motor. El par es comandado por el voltaje \( v \) aplicado al armature, que representa la entrada de control al sistema.

La relación entre el par y el voltaje aplicado está dada en el manual de Quanser como:

\[
v = i R_m + K_m K_g \omega
\]

Donde:
- \( i \) es la corriente del armature,
- \( R_m \) es la resistencia del motor,
- \( \omega \) es la velocidad angular del motor,
- \( K_m \) y \( K_g \) son parámetros constantes.

Por lo tanto, obtenemos la siguiente relación:

\[
i = \frac{v}{R_m} \left( \frac{K_m K_g}{m} \right)
\]

Ya que:

\[
i = \frac{\tau}{K_g K_m}
\]

Obtenemos la relación para el par:

\[
\tau = \frac{v}{R_m}
\]

Donde \( \theta = x_1 \), \( \beta = x_2 \), \( \dot{\theta} = x_3 \), y \( \dot{\beta} = x_4 \).
