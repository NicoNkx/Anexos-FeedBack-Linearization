### Tabla de Parámetros de la Planta

| Parámetro               | Símbolo   | Valor           |
|-------------------------|-----------|-----------------|
| Rigidez del Resorte      | \( K_s \) | 1.61 [N/m]      |
| Inercia del Hub          | \( J_h \) | 0.0021 [kg·m²]  |
| Masa del Brazo           | \( m \)   | 0.403 [kg]      |
| Constante Gravitacional  | \( g \)   | -9.81 [N/m]     |
| Altura del Centro de Masa| \( h \)   | 0.06 [m]        |
| Constante del Motor      | \( K_m \) | 0.00767 [N·rad/s]|
| Relación de Engranaje    | \( K_g \) | 70              |
| Inercia de la Carga      | \( J_l \) | 0.0059 [kg·m²]  |
| Resistencia del Motor    | \( R_m \) | 2.6 [Ω]         |

**Tabla 1**: Parámetros de la Planta

### Ecuaciones del Sistema

El sistema está representado por las siguientes ecuaciones:

\[
\dot{x}_1 = x_3
\]
\[
\dot{x}_2 = x_4
\]
\[
\dot{x}_3 = x_2 x_3 + \frac{v}{J_h R_m J_h}
\]
\[
\dot{x}_4 = x_2 + x_3 + \frac{v}{x_2} + \frac{J_l mgh}{J_l \sin(x_1 + x_2)}
\]

Definiendo \( u = v \), y eligiendo como salida la posición de la punta \( y = x_1 + x_2 \), el sistema ahora puede expresarse en la forma estándar de espacio de estados:

\[
\dot{x} = f(x) + g(x) u
\]
\[
y = h(x)
\]

Donde:

\[
f(x) =
\begin{pmatrix}
x_3 \\
x_4 \\
\frac{K}{2m} \\
\frac{K}{2g} \\
K_s x_2 + x_3 \\
\frac{J_h}{R_m J_h} \left( \frac{K_s}{J_h} + \frac{K_s}{J_l} \right) x_2 + \frac{K}{2m} + \frac{K}{2g} \\
mgh \\
Jl \sin(x_1 + x_2) \\
\end{pmatrix}
\]

\[
g(x) =
\begin{pmatrix}
0 \\
0 \\
\frac{K_m K_g}{R_m J_h} \\
\frac{K_m K_g}{R_m J_h}
\end{pmatrix}
\]

\[
h(x) = x_1 + x_2
\]
