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