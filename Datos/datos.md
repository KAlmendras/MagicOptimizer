# Datos 

Los datos que necesitamos se pueden obtener del conjunto de datos de Scryfall. Como los datos se actualizan a diario sera necesario realizar una única petición al día 
y como Scryfall proporciona un export de todas las cartas en formato JSONL se puede descargar previamente y procesarse de forma local.

Fuente: https://api.scryfall.com/bulk-data 

Para el problema planteado se necesitan principalmente los siguientes campos:
* Nombre e identificador de la carta (`name`, `oracle_id`).
* Coste y valor de maná (`mana_cost`, `cmc`).
* Identidad de color (`color_identity`).
* Legalidad por formato (`legalities`).
* Precio de mercado en euros (`prices.eur`).

un ejemplo seria:
{
  "oracle_id": "53236dd7-845a-444c-96d5-f41ed7325d8f",
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
para la creación de software, investigación o contenido de comunidad relacionado con Magic: The Gathering.

Las condiciones de uso de Scryfall no permiten usar su nombre o logotipos de forma que sugiera que el proyecto está respaldado por Scryfall, ni ofrecer los datos
tal cual sin aportar valor añadido (simple republicación o proxy de los datos). El proyecto cumple esta condición porque los datos se combinan con la lógica de negocio propia
descrita más arriba, y no se limita a mostrarlos.

Magic: The Gathering y los nombres de las cartas son marcas de Wizards of the Coast LLC. El uso de los datos de Scryfall no implica ningún tipo de afiliación o respaldo por 
parte de Wizards of the Coast ni de Scryfall.
