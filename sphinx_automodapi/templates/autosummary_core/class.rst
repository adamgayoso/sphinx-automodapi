{% if referencefile %}
.. include:: {{ referencefile }}
{% endif %}

{{ objname }}
{{ underline }}

.. currentmodule:: {{ module }}

.. autoclass:: {{ objname }}
   :show-inheritance:

   {% if '__init__' in methods %}
     {% set caught_result = methods.remove('__init__') %}
   {% endif %}

   {% block attributes_summary %}
   {% if attributes %}

   .. rubric:: Attributes Summary

   .. autosummary::
      :toctree: api/
   {% for item in attributes %}
      ~{{ fullname }}.{{ item }}
   {%- endfor %}

   {% endif %}
   {% endblock %}

   {% block methods_summary %}
   {% if methods %}

   .. rubric:: Methods Summary

   .. autosummary::
      :toctree: api/
   {% for item in methods %}
      ~{{ fullname }}.{{ item }}
   {%- endfor %}

   {% endif %}
   {% endblock %}
