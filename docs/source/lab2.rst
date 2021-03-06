
.. |vspace| raw:: latex

   \vspace{5mm}

.. _lab2:

*****************************
Lab 2: Stress transformations
*****************************

.. toctree::
   :maxdepth: 2

The objective of this lab is to:

      1. transform 2nd Piola-Kirchhoff stresses to Cauchy stresses.

      2. transform stresses and strains between fibre and reference coordinates.

The deformations that will be considered in this lab include uniaxial and equi-biaxial extension of an isotropic unit cube.

========
Revision
========

Before starting this lab, please be sure to have completed :ref:`Lab 1: Analysing deformation in isotropic materials <lab1>`.

===================================================================
Section 1: Transforming stresses from 2nd Piola-Kirchhoff to Cauchy
===================================================================


1. Start OpenCMISS and load the kinematics analysis project. Select "Model 1 (uniaxial extension of a unit cube)" from the drop down menu and click the "run" button.

|vspace|

2. Using the components of the 2nd Piola-Kirchhoff stress tensor :math:`(\boldsymbol{T})` and your deformation gradient tensor :math:`(\boldsymbol{F})` from step 5, determine the Cauchy components of the stress tensor :math:`(\boldsymbol{\Sigma})` (Don't forget the Jacobian :math:`(J)`).

|vspace|

3. Select "Problem" from the menu bar and repeat step 1-2 for the remaining models in the kinematics analysis project.

|vspace|

Questions
---------

After you have completed the above exercises, answer the following questions:

a. In model 1, why are :math:`\Sigma_{22}` and :math:`\Sigma_{33}` zero. How do they relate to the deformation seen in the graphical window?

|vspace|

b. In model 3, why is :math:`\Sigma_{33}` negative?

|vspace|

c. In model 3, why are the off-diagonal components of :math:`\boldsymbol{\Sigma}` nonzero?

|vspace|

.. note::

  By the end of section 1 you should be able to:

    - derive the Cauchy stress tensor from the second Piola-Kirchhoff stress tensor.

    - relate the components of the Cauchy stress tensor to the underlying deformation.


=====================================================================
Section 2: Transforming stresses between different coordinate systems
=====================================================================

Uniaxial extension of a unit cube
---------------------------------

1. Consider the uniaxial deformation shown in the figure below, where the fibre (material) axes are aligned with the reference axes:

  .. image:: images/uniaxial_0_degrees_fibres.png

  In the screenshot:
    - the undeformed (reference) configuration of the unit cube is shown in red;
    - the deformed (current) configuration is shown in green; and
    - the gold arrows indicate the direction of the fibres in the material. They **do not** indicate the direction of loading.

  |vspace|

  This deformation is described by the following equations:

  .. math::

    x_1 = \frac{3}{2}X_1 ~~~~ x_2 = \sqrt{\frac{2}{3}}X_2 ~~~~ x_3 = \sqrt{\frac{2}{3}}X_3

|vspace|

2. Write down:

  - the deformation gradient tensor, :math:`\boldsymbol{F}=\frac{\partial\boldsymbol{x}}{\partial\boldsymbol{X}}`
  - the right Cauchy-Green deformation tensor, :math:`\boldsymbol{C}` and
  - the Green-Lagrange strain tensor. Label this as :math:`\boldsymbol{E}_{ref}` (to indicate that it is defined with respect to the spatial reference coordinates).

  .. Note::

      This is the same deformation used in Model 1 in Lab 1, so you should not need to re-do these calculations.

      For this model, the second Piola-Kirchhoff stress tensor with respect to both the reference and fibre axes is:

      .. math::

        \boldsymbol{T_{ref}} = \boldsymbol{T_{fib}} = 
        \begin{bmatrix}
          440.5  & 0       & 0 \\
          0      & 0       & 0 \\
          0      & 0       & 0
        \end{bmatrix}

      While the deformation in Model 1 of the kinematics analysis project in OpenCMISS is the same as that considered here (i.e. they both describe the same uniaxial deformation), the stress tensor in the simulation results pane **is different** because the kinematics analysis project and the example above use different constitutive relations to represent the mechanical response of the material.

|vspace|

.. _tensor_transformations:

Isotropic deformation with respect to rotated fibre axes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

3. Now consider the same deformation, except that the fibre (material) axes are no longer aligned with the reference axes. They are now rotated anticlockwise by an angle of :math:`\theta=30` degrees from the :math:`X_{1}` axis (in the :math:`X_{1}`-:math:`X_{2}` plane), as shown in the figure below.

  .. image:: images/uniaxial_30_degrees_fibres.png

|vspace|

  For the following exercises, you are asked to transform strain and stress tensors between the reference coordinates and the fibre (material) coordinate systems using the generalised rotational transform given by:

  .. math::

    \boldsymbol{A}_{fib} = \boldsymbol{Q}^{T} \boldsymbol{A}_{ref} \boldsymbol{Q}

  where :math:`\boldsymbol{A}_{ref}` and :math:`\boldsymbol{A}_{fib}` are the tensor quantities (strain or stress) defined with respect to the reference and fibre axes, respectively, and :math:`\boldsymbol{Q}` is the orthogonal rotation matrix:

  .. math::

      \boldsymbol{Q} = 
      \begin{bmatrix}
        \cos(\theta) & -\sin(\theta) & 0  \\
        \sin(\theta) &  \cos(\theta) & 0  \\
        0              &  0              & 1
      \end{bmatrix}

|vspace|

4. Determine the Green-Lagrange strain tensor components with respect to the fibre axes (:math:`\boldsymbol{E}_{fib}`) via the appropriate tensor transformation (see Step 3).

|vspace|

5. Explain similarities/differences between :math:`\boldsymbol{E}_{fib}` and :math:`\boldsymbol{E}_{ref}` for this model.

|vspace|

6. Using the following values for the second Piola-Kirchhoff stress components with respect to the fibre axes (:math:`\boldsymbol{T}_{fib}`):

  .. math::

    \boldsymbol{T_{fib}} = 
    \begin{bmatrix}
      330.345   & -190.725  & 0 \\
      -190.725  & 110.115   & 0 \\
      0       & 0       & 0
    \end{bmatrix}

  determine the second Piola-Kirchhoff stress components with respect to the reference coordinate axes (:math:`\boldsymbol{T}_{ref}`) via the appropriate tensor transformation (see Step 3).

|vspace|

7. Explain similarities/differences between :math:`\boldsymbol{T}_{fib}` and :math:`\boldsymbol{T}_{ref}` for this model.

|vspace|

8. What would you expect from the analysis in steps 4-7 if the fibre angle was changed from :math:`\theta=30` degrees to :math:`\theta=45` degrees, or to :math:`\theta=90` degrees for this model?  Explain the differences/similarities of the stress tensors :math:`\boldsymbol{T}_{fib}` and :math:`\boldsymbol{T}_{ref}` for this uniaxial deformation model.

  .. note::

    You should not need to do any calculations to answer this questions, but if you would like the extra practice, perform steps 4-7 using:

    :math:`\theta=45` degrees, where the second Piola-Kirchhoff stress tensor with respect to the fibre axes is:

      .. math::

        \boldsymbol{T_{fib}} = 
        \begin{bmatrix}
          220.2   & -220.2  & 0 \\
          -220.2  & 220.2   & 0 \\
          0       & 0       & 0
        \end{bmatrix}

    and/or :math:`\theta=90` degrees, where the second Piola-Kirchhoff stress tensor with respect to the fibre axes is:

      .. math::

        \boldsymbol{T_{fib}} = 
        \begin{bmatrix}
          0      & 0       & 0 \\
          0      & 440.5   & 0 \\
          0      & 0       & 0
        \end{bmatrix}

|vspace|

.. _isotropic_biaxial_extension_of_unit_cube:

Equi-biaxial extension of a unit cube
-------------------------------------

9. Start OpenCMISS and load the stress analysis project (described in the :ref:`Starting OpenCMISS <starting-OpenCMISS>` section).

|vspace|

10. Select "Model 1 (Equi-biaxial extension of unit cube, isotropic, 0 degree fibre rotation)" from the drop down menu and click the "run" button (screenshots of this procedure are shown in the :ref:`Running models in OpenCMISS <running-models-in-OpenCMISS>` section).

|vspace|

11. After a short time, the model should have solved and the simulation results will appear in the 3D graphics window as shown in the screenshot below.

  .. image:: images/lab2_model1.png

  |vspace|

  In this graphical window:

      - the undeformed (reference) configuration of the unit cube is shown in red, and
      - the deformed (current) configuration is shown in green (:math:`x_{1}`, :math:`x_{2}`, :math:`x_{3}` components of the deformed coordinates are shown at the corners of the model.
      - ignore the gold arrows for now - these will be needed later.

  The model in the 3D graphics window can be rotated (click-drag-left-mouse button), translated (click-drag-middle-mouse button), or zoomed (click-drag-middle-mouse button).

|vspace|


12. This equi-biaxial deformation is incompressible (i.e. maintains constant volume) described by the equations:

  .. math::

    x_1 &= \frac{5}{4}X_1 ~~~~ x_2 &= \frac{5}{4}X_2 ~~~~ x_3 &= \frac{16}{25}X_3

|vspace|

13. Write down:

  - the deformation gradient tensor (:math:`\boldsymbol{F}=\frac{\partial\boldsymbol{x}}{\partial\boldsymbol{X}}`),
  - the right Cauchy-Green deformation tensor (:math:`\boldsymbol{C}`), and
  - Green-Lagrange strain tensor (:math:`\boldsymbol{E}`) (label this :math:`\boldsymbol{E}_{ref}`).

  .. Note::

      This is the same deformation used in Model 2 of Lab 1, so you should not need to re-do these calculations.

|vspace|

Isotropic deformation with respect to rotated fibre axes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

14. Return to the model selection drop down menu and select/run "Model 3 (Equi-biaxial extension of unit cube, isotropic, 30 degree fibre rotation)". This model is similar to the previous models, except that the fibre (material) axes are no longer aligned with the reference (spatial) axes. For this model, the fibre axis is rotated anticlockwise by an angle of :math:`\theta=30` degrees from the :math:`X_{1}` axis (in the :math:`X_{1}`-:math:`X_{2}` plane). When visualising these models, the gold arrows in the graphics window indicate the direction of the fibre axis (along which the first material coordinate is defined), and the :math:`X_{1}`-:math:`X_{2}` plane indicates the orientation of the flat laminar sheet.

|vspace|

15. Determine the Green-Lagrange strain tensor components with respect to the fibre axes (:math:`\boldsymbol{E}_{fib}`) using the approach in Section 2.

|vspace|

16. Check your answers to Step 15 against the simulation results.

  .. Note::

      Drag the right edge of the 3D graphics window to reveal the stress and strain tensors associated with the simulation in fibre and reference coordinates. See :ref:`this link <opening_simulation_pane>` for an example on how to open this pane.

|vspace|

17. Explain similarities/differences between :math:`\boldsymbol{E}_{fib}` and :math:`\boldsymbol{E}_{ref}` for this model.

|vspace|

18. From the solution output, write down  :math:`\boldsymbol{T}_{fib}` (the second Piola-Kirchhoff stress tensor with respect to the fibre axes). Use this to determine the second Piola-Kirchhoff stress components with respect to the reference coordinate axes (:math:`\boldsymbol{T}_{ref}`) via the approach Section 2.

|vspace|

19. Check your answers to Step 18 against the simulation results.

|vspace|

20. Explain similarities/differences between :math:`\boldsymbol{T}_{fib}` and :math:`\boldsymbol{T}_{ref}` for this model.

|vspace|

21. What would you expect from the analysis in steps 15-20 if the fibre angle was changed from :math:`\theta=30` degrees to :math:`\theta=45` degrees, or to :math:`\theta=90` degrees for this equi-biaxial deformation model?  Explain the differences/similarities between the two strain, and (separately) between the two stress tensors for this model.

  .. note::

    You should not need to do any calculations to answer this questions, but if you need the extra practice, perform steps 15-20 with :math:`\theta=45` degrees by selecting the Model 4 from the "run" menu.

|vspace|

====================
Section 3: Questions
====================

After you have completed the exercises above, consider the following questions: 

a. How do changes in :math:`\boldsymbol{E}_{ref}` for different fibre angles (:math:`\theta`) in the equi-biaxial deformation compare with the changes seen in the uniaxial deformation.

b. How do changes in :math:`\boldsymbol{E}_{fib}` for different fibre angles (:math:`\theta`) in the equi-biaxial deformation compare with the changes seen in the uniaxial deformation.

c. How do changes in :math:`\boldsymbol{T}_{ref}` for different fibre angles (:math:`\theta`) in the equi-biaxial deformation compare with the changes seen in the uniaxial deformation.

d. How do changes in :math:`\boldsymbol{T}_{fib}` for different fibre angles (:math:`\theta`) in the equi-biaxial deformation compare with the changes seen in the uniaxial deformation.

e. Will the invariants of :math:`\boldsymbol{C}` be the same or different when calculated with respect to fibre or reference coordinates?

|vspace|

.. note::

  By completing this lab, you should be able to:

    - analyse large deformation kinematics with respect to reference or material coordinates for isotropic materials.

    - analyse stress tensors with respect to spatial or material coordinates for isotropic materials.


Here are the solutions to :ref:`Step 8<lab2_section2_step8_solutions>` and :ref:`Step 21<lab2_section2_step21_solutions>` of Section 2.
