===========
Instalacion
===========

Para poder usar esta libreria es necsario primero instalarla, usa pip

.. code-block:: console

    pip install Paquete-optimizacion-byzamm079

Une vez hecho esto puedes mandar a llamr las funciones como en el siguiente ejemplo:

.. code-block:: python

    from metod_univariable import metodos_elim_regiones
    from metod_univariable import metodos_basado_derivada

    from metod_multivariable import metodos_directos
    from metod_multivariable import metodos_gradiente

    from funciones_prueba import func_objetivo
    import numpy as np
    x = np.array([1.0,3.0])
    print(func_objetivo.sphere_function(X=x))

    print(metodos_directos.simplex_search_meth(x,func_objetivo.sphere_function))