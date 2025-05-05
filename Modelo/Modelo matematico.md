## Descripción del sistema: Manipulador de un solo enlace con articulación flexible en plano vertical

En esta sección, se considera un manipulador de un solo enlace con una articulación flexible operando en un plano vertical.  
La principal diferencia con respecto al modelo del manipulador con articulación flexible en un plano horizontal, considerado en el experimento anterior, es la presencia de la gravedad, la cual introduce una no linealidad en las ecuaciones de la dinámica.

El modelo matemático de la dinámica del enlace con articulación flexible en posición vertical se obtiene fácilmente a partir de las ecuaciones de movimiento de Lagrange.

Es evidente que el sistema tiene dos grados de libertad, correspondientes a:

- La rotación del eje del motor respecto a un sistema de coordenadas fijo a la base.
- La rotación de la articulación flexible a la cual está unido el enlace respecto al motor.

Las coordenadas generalizadas son, por tanto:

- La posición angular del motor $\\theta$.
- El desplazamiento angular de la articulación flexible $\\beta$.

La energía potencial y cinética del sistema están dadas respectivamente por:

$$ K = K_h + K_l ; V = V_g + V_s $$

Donde:

- Energía potencial gravitacional (Vg):

  $$ V_g = m g h \cos(\theta + \beta) $$

- Energía potencial elástica del resorte de la articulación (Vs):

  $$ V_s = \frac{1}{2} K_s \beta^2 $$

- Energía cinética del motor (Kh):

  $$ K_h = \frac{1}{2} J_h (\dot{\theta})^2 $$

- Energía cinética del enlace (Kl):

  $$ K_l = \frac{1}{2} J_l (\dot{\theta} + \dot{\beta})^2 $$


### Energía Potencial y Energía Cinética

Donde:
- **Vg** es la energía potencial debido a la gravedad.
- **Vs** es la energía potencial debida a los resortes.
- **Kh** es la energía cinética del hub.
- **Kl** es la energía cinética de la carga.
- **m** es la masa del eje.
- **g** es la constante de gravedad.
- **h** es la altura del centro de gravedad del enlace con respecto a la posición de reposo.
- **J_h** es la inercia en la salida del motor.
- **J_l** es la inercia del brazo.
- **K_s** es la rigidez del resorte.

El valor de la constante **K_s** depende de la forma en que los resortes están conectados al enlace. Según el manual de Quanser, la expresión para **K_s** es:

$$
K_s = \\frac{2R}{D} \\left( \\frac{3}{2} \\left( Dd - Rr \\right)^{\\frac{2}{3}} \\right) F_r + \\left( Dd - DLd + Rr \\right)^{\\frac{2}{3}} L
$$

Donde:
- **R** es el punto de anclaje del brazo.
- **d** es el punto de anclaje del cuerpo "Y".
- **r** es el punto de anclaje del cuerpo "X".
- **K** es la rigidez del resorte.
- **F_r** es la fuerza restauradora del resorte.
- **L** es la longitud del resorte en reposo.
- **D** es el valor constante del resorte (según el manual de Quanser).

### Lagrangiana y Ecuaciones de Movimiento

La Lagrangiana está dada por:

$$
L = K - V
$$

Las ecuaciones de movimiento de Lagrange se expresan como:

$$
\\frac{d}{dt} \\left( \\frac{\\partial L}{\\partial \\dot{\\beta}} \\right) - \\frac{\\partial L}{\\partial \\beta} = 0
$$

$$
\\frac{d}{dt} \\left( \\frac{\\partial L}{\\partial \\dot{\\theta}} \\right) - \\frac{\\partial L}{\\partial \\theta} = \\tau
$$

Donde $\\tau$ es el par de torsión producido por el motor. El par es comandado por el voltaje $v$ aplicado al armature, que representa la entrada de control al sistema.

La relación entre el par y el voltaje aplicado está dada en el manual de Quanser como:

$$
v = i R_m + K_m K_g \\omega
$$

Donde:
- $i$ es la corriente del armature,
- $R_m$ es la resistencia del motor,
- $\\omega$ es la velocidad angular del motor,
- $K_m$ y $K_g$ son parámetros constantes.

Por lo tanto, obtenemos la siguiente relación:

$$
i = \\frac{v}{R_m} \\left( \\frac{K_m K_g}{m} \\right)
$$

Ya que:

$$
i = \\frac{\\tau}{K_g K_m}
$$

Obtenemos la relación para el par:

$$
\\tau = \\frac{v}{R_m}
$$

Donde $\\theta = x_1$, $\\beta = x_2$, $\\dot{\\theta} = x_3$, y $\\dot{\\beta} = x_4$.

### Tabla de Parámetros de la Planta

| Parámetro               | Símbolo   | Valor           |
|-------------------------|-----------|-----------------|
| Rigidez del Resorte      | $K_s$     | 1.61 [N/m]      |
| Inercia del Hub          | $J_h$     | 0.0021 [kg·m²]  |
| Masa del Brazo           | $m$       | 0.403 [kg]      |
| Constante Gravitacional  | $g$       | -9.81 [N/m]     |
| Altura del Centro de Masa| $h$       | 0.06 [m]        |
| Constante del Motor      | $K_m$     | 0.00767 [N·rad/s]|
| Relación de Engranaje    | $K_g$     | 70              |
| Inercia de la Carga      | $J_l$     | 0.0059 [kg·m²]  |
| Resistencia del Motor    | $R_m$     | 2.6 [Ω]         |

**Tabla 1**: Parámetros de la Planta

### Ecuaciones del Sistema

El sistema está representado por las siguientes ecuaciones:

$$
\\dot{x}_1 = x_3
$$
$$
\\dot{x}_2 = x_4
$$
$$
\\dot{x}_3 = x_2 x_3 + \\frac{v}{J_h R_m J_h}
$$
$$
\\dot{x}_4 = x_2 + x_3 + \\frac{v}{x_2} + \\frac{J_l mgh}{J_l \\sin(x_1 + x_2)}
$$

Definiendo $u = v$, y eligiendo como salida la posición de la punta $y = x_1 + x_2$, el sistema ahora puede expresarse en la forma estándar de espacio de estados:

$$
\\dot{x} = f(x) + g(x) u
$$
$$
y = h(x)
$$

Donde:

$$
f(x) =
\\begin{pmatrix}
x_3 \\\\
x_4 \\\\
\\frac{K}{2m} \\\\
\\frac{K}{2g} \\\\
K_s x_2 + x_3 \\\\
\\frac{J_h}{R_m J_h} \\left( \\frac{K_s}{J_h} + \\frac{K_s}{J_l} \\right) x_2 + \\frac{K}{2m} + \\frac{K}{2g} \\\\
mgh \\\\
Jl \\sin(x_1 + x_2) \\\\
\\end{pmatrix}
$$

$$
g(x) =
\\begin{pmatrix}
0 \\\\
0 \\\\
\\frac{K_m K_g}{R_m J_h} \\\\
\\frac{K_m K_g}{R_m J_h}
\\end{pmatrix}
$$

$$
h(x) = x_1 + x_2
$$

