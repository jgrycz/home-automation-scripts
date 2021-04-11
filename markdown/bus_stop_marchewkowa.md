{% set departs =  state_attr("sensor.impk_marchewkowa_to_krzyki", "list")|list + state_attr("sensor.impk_marchewkowa_from_krzyki", "list")|list %}
{% for departure in departs|sort(attribute="departure")  %}
{%- if loop.first %}||Odjazd|Linia|Kierunek||
|---|---|:---:|---|---| {%- endif %}
|{%- if departure.delay != 0 -%} ![Image](/local/icons/clock-alert-outline.png){% endif %}| {{departure.original_departure }} | {{ departure.line }} | {{ departure.direction }} | {%- if departure.delay != 0 -%} **+{{ (departure.delay / 60)|int }}m**{% endif %}|
{%- endfor %}
