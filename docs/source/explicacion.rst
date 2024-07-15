===========
Explicacion
===========

Aqui se van a detallar mas sobre las funcione que tiene la libreria de 
optimizacion

Método de división de intervalos por la mitad

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


Búsqueda de Fibonacci

.. code-block:: python

    def fibonacci_search(a,b,n,funcion):
            #step 1
            L = b-a
            k=2
            while k != n:
                #step 2
                Lk = fibonacci(n-k+1)/fibonacci(n+1)
                x1 = a + Lk
                x2 = b - Lk
                #step 3
                fx1 = funcion(x1)
                fx2 = funcion(x2)
                if fx1 > fx2:
                    a = x1
                if fx1 < fx2:
                    b = x2
                if fx1 == fx2:
                    a = x1
                    b = x2
                #step 4
                k = k+1
            return [x1,x2]


Golden Section Search 

.. code-block:: python

        def golden_section_search(funcion, a, b, epsilon):
                
                golden = 0.618
                golden2 = 1 - golden

                w1 = a + golden2 * (b - a)
                w2 = a + golden * (b - a)

                f_x1 = funcion(w1)
                f_x2 = funcion(w2)

                while b - a > epsilon:
                    
                    if f_x1 < f_x2:
                        b = w2
                        w2 = w1
                        w1 = a + golden2 * (b - a)
                        f_x2 = f_x1
                        f_x1 = funcion(w1)
                    else:
                        a = w1
                        w1 = w2
                        w2 = a + golden * (b - a)
                        f_x1 = f_x2
                        f_x2 = funcion(w2)

                return [a, b]


Metodos basados en la derivada

Newton Raphson Method

.. code-block:: python
        def newton_raphson_method(funcion, i_guess, delta_fun, epsilon):
                x = i_guess
                k = 1
                max_iter=10000
                while k < max_iter:
                    #step1
                    delta_x = delta_fun(x)
                    f_derivada1 = central_difference_1(funcion, x, delta_x)
                    #step2
                    f_derivada2= central_difference_2(funcion, x, delta_x)
                    
                    if abs(f_derivada1) < epsilon:
                        return x
                    #step 3
                    x_k1 = x - f_derivada1 / f_derivada2
                    #step 4
                    if abs(x_k1 - x) < epsilon:
                        return x_k1
                    
                    x = x_k1
                    k += 1
                
                return x


Metodo Biseccion

.. code-block:: python
    def bisection_method(funcion, a, b, epsilon, delta_x):
            x1 = a
            x2 = b
            max_iter=10000
            if (central_difference_1(funcion, a, delta_x) < 0) and (central_difference_1(funcion, b, delta_x) > 0):
                epsilon = epsilon
            else:
                raise ValueError("La función no cumple con la condición")
            
            iteraciones = 0

            while abs(x1 - x2) > epsilon and iteraciones < max_iter:
                z = (x1 + x2) / 2
                f_z = central_difference_1(funcion, z, delta_x)

                if abs(f_z) <= epsilon:
                    return z, z 

                if f_z < 0:
                    x1 = z
                else:
                    x2 = z

                iteraciones += 1

            return [x1, x2]