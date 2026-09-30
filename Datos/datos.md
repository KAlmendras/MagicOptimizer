# Datos 

Los datos que necesitamos se pueden obtener del conjunto de datos de Scryfall. Como los datos se actualizan a diario sera necesario realizar una única petición al día 
y como Scryfall proporciona un export de todas las cartas en formato JSONL se puede descargar previamente y procesarse de forma local.

Fuente: https://api.scryfall.com/bulk-data 

Para el problema planteado se necesitan principalmente los siguientes campos:
* Identificador de la carta con el nombre  (`name`) para cruzarla con la tabla de cartas candidatas y las cartas del mazo.
* Coste y valor de maná (`mana_cost`, `cmc`) para calcular el ajuste de la curva de mana en la puntuación.
* Identidad de color  (`color_identity`) para el filtro de color respecto al mazo.
* Legalidad por formato (`legalities`) para el filtro de legalidad del formato de juego.
* Precio de mercado en euros (`prices.eur`) para el filtro y restricción del presupuesto.

un ejemplo seria:
{
  "name": "Rhystic Study",
  "mana_cost": "{2}{U}",
  "cmc": 3.0,
  "color_identity": ["U"],
  "legalities": { "commander": "legal" },
  "prices": {  "eur": "38.50" }
}

Los roles funcionales, el mazo actual, la lista de cartas candidatas y el presupuesto son datos que tendria que ingresar el usuario segun su conocimiento del mazo y estrategia.

## Licencia de los datos

Los datos utilizados proceden de Scryfall (https://scryfall.com), que los ofrece de forma gratuita al amparo de la Fan Content Policy de Wizards of the Coast,
para la creación de software, investigación o contenido de comunidad relacionado con Magic: The Gathering.  https://company.wizards.com/en/legal/fancontentpolicy

El proyecto cumple esta condición porque los datos se combinan con la lógica de negocio propia descrita más arriba, y no se limita a mostrarlos.

MagicOptimizer es contenido de fan permitido bajo la Fan Content Policy.No aprobado/respaldado por Wizards. Parte de los materiales usados son propiedad de Wizards of the Coast.
©Wizards of the Coast LLC.
