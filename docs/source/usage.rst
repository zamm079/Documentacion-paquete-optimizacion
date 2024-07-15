Usage
=====

.. _installation:

Instalacion
------------

Para poder usar la libreria primero se debe instalar, usa pip:

.. code-block:: console

   pip install Paquete-optimizacion-byzamm079


Como llamarlo
----------------

Para poder mandar a llamr las funciones debes de usar el 
comando from ``from metod_univariable import metodos_elim_regiones``

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

