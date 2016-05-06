Example Scripts
------------------

For simple Primer Design tasks, follow this example:

.. code-block:: python
   :linenos:

    import primerize

    prm_1d = primerize.Primerize_1D()
    job_1d = prm_1d.design('TTCTAATACGACTCACTATAGGCCAAAGGCGUCGAGUAGACGCCAACAACGGAAUUGCGGGAAAGGGGUCAACAGCCGUUCAGUACCAAGUCUCAGGGGAAACUUUGAGAUGGCCUUGCAAAGGGUAUGGUAAUAAGCUGACGGACAUGGUCCUAACCACGCAGCCAAGUCCUAAGUCAACAGAUCUUCUGUUGAUAUGGAUGCAGUUCAAAACCAAACCGUCAGCGAGUAGCUGACAAAAAGAAACAACAACAACAAC', MIN_TM=60.0, NUM_PRIMERS=None, MIN_LENGTH=15, MAX_LENGTH=60, prefix='P4P6_2HP')
    if job_1d.is_success:
        print job_1d

    prm_2d = primerize.Primerize_2D()
    job_2d = prm_2d.design(job_1d, offset=-51, which_muts=range(102, 261 + 1), which_lib=1)
    if job_2d.is_success:
        print job_2d
        job_2d.save()

    prm_3d = primerize.Primerize_3D()
    job_3d = prm_3d.design(job_1d, offset=-51, structures=['...........................((((((.....))))))...........((((((...((((((.....(((.((((.(((..(((((((((....)))))))))..((.......))....)))......)))))))....))))))..)).))))((...((((...(((((((((...)))))))))..))))...)).............((((((.....))))))......................'], N_mutations=1, which_lib=1, is_single=True, is_fillWT=True)
    if job_3d.is_success:
        print job_3d
        job_3d.save()

For advanced users, the returned ``Design_Single`` and ``Design_Plate`` result classes offer methods for ``get()``, ``save()`` and ``echo()``:

.. code-block:: python
   :linenos:

    MIN_TM = job_1d.get('MIN_TM')
    print job_1d.get('MISPRIME')
    print job_1d.echo('WARNING')
    if job_1d.is_success:
        job_1d.save(path='result/', name='Primer')

    LIB = job_2d.get('which_lib')
    N_PRIMER = job_2d.get('N_PRIMER')
    print job_2d.get('CONSTRUCT')
    if job_2d.is_success:
        print job_2d.echo('region')
        job_2d.save('assembly', path='result/', name='Lib')

    N_PLATE = job_3d.get('N_PLATE')
    if job_3d.is_success:
        print job_3d.echo('plate')
        print repr(job_3d)

Besides ``design()``, the ``Primerize_1D``, ``Primerize_2D``, and ``Primerize_3D`` worker classes offer methods for ``get()``, ``set()``, and ``reset()``:

.. code-block:: python
   :linenos:

    COL_SIZE = prm_1d.get('COL_SIZE')
    prm_1d.set('MIN_LENGTH', 30)
    prm_1d.reset()

There are also ``Assembly``, ``Mutation``, ``Construct_List``, and ``Plate_96Well`` helper classes. For more details, please refer to the **Documentation**.
