## Descripción del sistema: Manipulador de un solo enlace con articulación flexible en plano vertical

En esta sección, se considera un manipulador de un solo enlace con una articulación flexible operando en un plano vertical.  
La principal diferencia con respecto al modelo del manipulador con articulación flexible en un plano horizontal, considerado en el experimento anterior, es la presencia de la gravedad, la cual introduce una no linealidad en las ecuaciones de la dinámica.

El modelo matemático de la dinámica del enlace con articulación flexible en posición vertical se obtiene fácilmente a partir de las ecuaciones de movimiento de Lagrange.

Es evidente que el sistema tiene dos grados de libertad, correspondientes a:

- La rotación del eje del motor respecto a un sistema de coordenadas fijo a la base.
- La rotación de la articulación flexible a la cual está unido el enlace respecto al motor.

Las coordenadas generalizadas son, por tanto:

- La posición angular del motor $\theta$.
- El desplazamiento angular de la articulación flexible $\beta$ (ver Figura 5).

La energía potencial y cinética del sistema están dadas respectivamente por:


K = Kh + Kl ; V = Vg + Vs

Donde:

- Energía potencial gravitacional (Vg):

  Vg = m * g * h * cos(θ + β)

- Energía potencial elástica del resorte de la articulación (Vs):

  Vs = (1/2) * Ks * β^2

- Energía cinética del motor (Kh):

  Kh = (1/2) * Jh * (θ_dot)^2

- Energía cinética del enlace (Kl):

  Kl = (1/2) * Jl * (θ_dot + β_dot)^2

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
