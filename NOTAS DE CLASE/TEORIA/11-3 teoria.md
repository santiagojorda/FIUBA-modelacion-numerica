# Clase 11/03/2025

> Como transformar un problema matematico a un problema numerico
- lo hago mediante un metodo numerico
- tengo un problema matematico y no lo puedo resolver, por ende utilizo un M.N que me lleve a una aproximacion
- siempre que aproximo con metodo numerico, voy a tener errores
- Si tengo un problema matematico y puedo calcularlo, no hace falta aproximarlo, ya tengo su solucion

### Metodo numerico
- Siempre que no pueda calcular un problema matematico, puedo llegar a una solucion aproximada, la cual tiene un error..
- Todo metodo numerico tiene que poder saber la cota de error

### Cota de error
- es el valor mas grande que puede tomar ese numero

### Algoritmo (para un problema numerico)
- Receta para transformar los datos de entrada para obtener los datos de salida
- es la descripcion detallada de como trabajar con dicho metodo numerico

### Las propiedades matematicas cambian
- Al tener errores hay algunas propiedades estas cambian

### Teorema de Taylor
> aproximamos una funcion trigonometrica

- $f \in C^m [a,b]$, $f^{m+1} \exist [a,b)$ , $x_0 \in [a,b]$
- $f_(x) = P_m(x) + R_m(x)$
- el teorema me da el polinomio antes de calcular
- $\forall x_0 \in [a,b] \exist$ $S(x)$ esta entre $x_0$ y $x$
![alt text](/NOTAS%20DE%20CLASE/IMAGENES/teorema%20de%20tylor.png)
- en dicho punto yo conozco todas sus valores y sus derivadas
- $P_m(x) = F(x_0) + f'(x_0) (x-x_0) + \frac{f''(x_0)}{2!}(x-x_0)^2 + ... + \frac{f^m(x_0)}{m}(x-x_0)^m$

Definicion:
$$P_m(x) = \sum^{m}_{k=0}\frac{f^k(x_0)(x-x_0)^k}{k!}$$

> vamos a tratar de obtener de forma numerica el m
> el teorema de Taylor me va a dar la expresion de $R_m(x)

- $R_m(x) = \frac{f^{m+1}}{(m+1)!} (x-x_0)^{(m+1)}$

> vamos a buscar una cota de $R_m(x)$

#### Aproximacion de $cos(x)$ por un polinomio de Taylor

- $f(x) = cos(x)$
- $x_0 = 0$
- $m=2, P_2(x)$

> aca estoy usando un $x_0$ que es conocido

- $f(x_0) = cos(0) = 1$
- $f'(x) = -sen(x)$, $f'(x_0) = -sen(0) = 0$
- $f''(x) = -cos(x)$, $f''(x_0) = -cos(0) = -1$

> quedando asi

$$P_2(x) = 1 + 0 + \frac{-1}{2} (x-0)^2 = 1 - \frac{x^2}{2}$$
![alt text](/NOTAS%20DE%20CLASE//IMAGENES/20250311-8.png)

> el polinomio de taylor de grado 2 es una parabola
> esta aproxima muy bien a la funcion cerca del entorno del 0
![alt text](//NOTAS%20DE%20CLASE/IMAGENES/20250311-1.png)

> Tiene 4 raices por ser de grado 4
> aproxima mejor a la funcion
![alt text](//NOTAS%20DE%20CLASE/IMAGENES/20250311-2.png)

> las cotas que estan en gris
> las comparo con el error en azul
> a veces exageran el valor, pero no importa, es mejor eso que nada
![alt text](//NOTAS%20DE%20CLASE/IMAGENES/20250311-3.png)

> vemos ahora la diferencia es mas chica
> en los valores cercanos a 0, la cota es casi nula
![alt text](//NOTAS%20DE%20CLASE/IMAGENES/20250311-4.png)

---

### Propagacion de Errores (ejemplo 1.1)

- Ejmeplo $w = \frac{xy}{\sqrt{z}}$
- Valores medidos: $\hat{x}, \hat{y}, \hat{z}$
- $\hat{w} = \frac{\hat{x}\hat{y}}{\sqrt{\hat{z}}}$

cada variable se definen como:

- $x=\hat{x} + \pm \Delta{x}$
- $y=\hat{y} + \pm \Delta{y}$
- $z=\hat{z} + \pm \Delta{z}$

 calculo $\Delta{w}$

$$ \hat{z} - \Delta{z} \le z \le \hat{z} + \Delta{z}$$
donde $\Delta{z}$ de la derecha es cota y $z$ es el valor real desconocido

> si me dan 
> $x=2.0 + \pm 0.1$
> $y=3.0 + \pm 0.2$
> $z=1.0 + \pm 0.1$

$\hat{w} = \frac{2 \cdot 3^2}{1} = 2 \cdot 9 = 18$
$w_{max} = \frac{2.1 (3.2)^2}{\sqrt{0.9}} \approx 22.63$
> la diferencia entre $\hat{w}$ y la cota es de 4.63 

$w_{min} = \frac{1.9 (2.8)^2}{\sqrt{1.1}} \approx 14.2$
> la diferencia entre $\hat{w}$ y la cota es de 3.8 

entonces puedo poner como cota $\Delta{w} \approx 5$

### Programacion de errores (1.2)
- $y = (x_1 , x_2 , ... , x_m)$
- $x_i = \hat{x} + e_i$
- $|e_i| \le \Delta{x_i}$

quiero calcular con taylor
como conozco la medicion, en este caso es x_0
hago todo en base a ese valor

$$y(x_1 , x_2 , ... , x_m) = \hat{y} = y(\hat{x_1} , \hat{x_2} , ... , \hat{x_m})$$

hay que hacer taylor con derivadas parciales y las voy a evaluar en ${\hat{x}}$ -> esto es un vector de __$n$ componentes__
- $\hat{x} = (\hat{x_1} , \hat{x_2} , ... , \hat{x_m})$

> estoy estimando los errores con taylor de grado 1
> si resolvemos nos va a dar una cota mejor que la calculada en el ejercicio anterior
![alt text](//NOTAS%20DE%20CLASE/IMAGENES/20250311-5.png)

### Error relativo

$$ \epsilon = \frac{e}{x}$$

- Error relativo: $\epsilon$ (sin unidades)
- Error absoluto: $e$ (con unidades)
- Valor: $x$

> El error absoluto solo no me dice nada, pero el relativo me dice que tanto se aproxima al valor

Ejemplo:
- $y = x_1 \cdot x_2$
- $x_1=\hat{x_1} + \pm \Delta{x_1}$
- $x_2=\hat{x_2} + \pm \Delta{x_2}$

> calculo de error absoluto $e_y$
![alt text](//NOTAS%20DE%20CLASE/IMAGENES/20250311-6.png)

> cota del error relativo $\frac{e_y}{y}$
![alt text](//NOTAS%20DE%20CLASE/IMAGENES/20250311-7.png)