:::{include} ../README.md
---
relative-docs: docs/
relative-images: True
---
:::

:::{toctree}
---
hidden: True
---

Overview <self>
getting_started

:::

<!--
The autosummary directive renders to rST,
so we must use eval-rst here
-->
:::{eval-rst}
.. raw:: html

    <div style="display: None">

.. autosummary::
   :recursive:
   :caption: API Reference
   :toctree: api/generated
   :nosignatures:

   {{cookiecutter.repo_name}}

.. raw:: html

    </div>
:::
