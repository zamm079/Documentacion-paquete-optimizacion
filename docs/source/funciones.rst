=========
Funciones
=========

Aqui se muestran las funciones que esta libreria tiene
para ofrecer


Métodos para funciones de una variable
======================================

Métodos de eliminación de regiones
-----------------------------------

- Método de división de intervalos por la mitad

    .. code-block:: python
        def interval_halving(a,b,e,funcion):
            #step 1
            Xm=(a+b)/2
            L=b-a
            while abs(L) > e:
                # step 2
                x1 = a + L /4 #a
                x2 = b - L /4 #b
                fx1 = funcion(x1)
                fx2 = funcion(x2)
                Fxm = funcion(Xm)
                #step 3
                if fx1 < Fxm:
                    b = Xm
                    Xm = x1
                else:
                    if fx2 < Fxm:
                        a = Xm
                        Xm=x2
                    else:
                        a = x1
                        b = x2
                L = b-a
                if abs(L) < e:
                    return [x1,x2]

- Búsqueda de Fibonacci
- Método de la sección dorada

Métodos basados en la derivada
------------------------------

- Método de Newton-Raphson
- Método de bisección
- Método de la secante

Métodos para funciones multivariadas
====================================

Métodos directos
----------------

- Caminata aleatoria
- Método de Nelder y Mead (Simplex)
- Método de Hooke-Jeeves

Métodos de gradiente
--------------------

- Método de Cauchy
- Método de Fletcher-Reeves
- Método de Newton