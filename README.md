# Related Projects

## Background

This extension already exists in the PPPs block of extensions. However, we propose to add it to the community extensions in order to directly link the contracts with their respective projects (when applies) in order to specify relevant attributes such as:

	•	The total investment amount.
	•	Projects’ specific localization (geolocation).


## Extension fields

This extension adds an array named relatedProjects and consists of the following fields and objects:

	•	Id - An externally provided identifier for the project. This might be drawn from a project’s register, or may be based on the canonical version of a project name. Project IDs should be unique to a publisher. URIs can be used.
	•	Title - The name of the project to which this contracting process relates. Some organizations maintain a registry of projects, and the data should use the name by which the project is known in that registry.
	•	Description - A short free text description of the project.
	•	Uri - A URI pointing to further information about this project.

An object named relatedProjects.sector with the following fields:

	•	Scheme - A classification should be drawn from an existing scheme or list of codes. This field is used to indicate the scheme/codelist from which the classification is drawn. For line item classifications, this value should represent a known Item Classification Scheme wherever possible.
	•	Id - The classification code drawn from the selected scheme.
	•	Description - A textual description or title for the code.
	•	uri - A URI to identify the code. In the event individual URIs are not available for items in the identifier scheme this value should be left blank.

An object named relatedProjects.additionalClassifications with the following fields:

	•	Scheme - A classification should be drawn from an existing scheme or list of codes. This field is used to indicate the scheme/codelist from which the classification is drawn. For line item classifications, this value should represent a known Item Classification Scheme wherever possible.
	•	Id - The classification code drawn from the selected scheme.
	•	Description - A textual description or title for the code.
	•	uri - A URI to identify the code. In the event individual URIs are not available for items in the identifier scheme this value should be left blank.

An array named relatedProjects.locations with the following fields and object:

	•	Description - A name or description of this location. This might include the name(s) of the location(s), or might provide a human readable description of the location to be covered. This description may be used in a user-interface.

Also contains an object relatedProjects.locations.geometry with the fields:

	•	Type - The type of geoJSON Geometry Objects being provided. To provide latitude and longitude use ‘point’, and enter an array of [latitude, longitude] as the value of coordinates field. Note the capitalization of type values - set in order to maintain compatibility with geoJSON.
	•	Coordinates – Array de coordinates: e.g. [37.42,-122.085].

And an object named relatedprojects.totalValue with the fields:

	•	Amount - Amount as a number.
	•	Currency - The currency for each amount should always be specified using the uppercase 3-letter currency code from ISO4217.

## Example

```json
"planning": [ 
{
	"relatedProjects": {
		"id": "13096500015",
		"title": "Modernización de la carretera federal MEX 180. Tramos San Andrés Tuxtla Catemaco y Cosoleacaque Jáltipan Acayucan. Primera Etapa.",
		"description": "Ampliar a 21.00 metros, para alojar 4 carriles de circulación, 2 para cada sentido, de 3.5 metros cada uno y acotamientos externos de 2.5 metros e internos de 0.5 metros",
		"uri": "http://nptp.hacienda.gob.mx/NPTP/mapaOp/detalle.html?ID_PPI=39005&CVE_PPI=13096500015&RAMO=9&tipo=SEG",
		"sector": {
			"id": "1",
			"description": "Proyecto de Inversiín de Infraestructura Económica",
			"scheme": "Tipo de Programa y Proyecto de Inversión",
			},
		"locations": {
			"id": "24",
			"description": "Municipio de San Andrés Tuxtla, Catemaco, Cosoleacaque, Jáltipan, Texistepec, Oluta y Acayucan el Estado de Veracruz. Ambos en la Mesoregión Sur sureste",
			"geometry": {
				"type": "Point",
				"coordinates": [17.99,-94.64],
				}
			}
		},
	"totalValue": {
		"amount": "2.186277614E9",
		"currency": "MXN"
		}
	}
],
"contracts": {
	"implementation": [
	{
		"relatedProjects": {
			"id": "13096500015",
			"title": "Modernización de la carretera federal MEX 180. Tramos San Andrés Tuxtla Catemaco y Cosoleacaque Jáltipan Acayucan. Primera Etapa.",
			"description": "Ampliar a 21.00 metros, para alojar 4 carriles de circulación, 2 para cada sentido, de 3.5 metros cada uno y acotamientos externos de 2.5 metros e internos de 0.5 metros",
			"uri": "www.exampleuri.com",	
			"metrics": {
				"id": "1",
				"title": "kilómetros repavimentados a la semana",
				"description": "Número de kilómetros repavimentados entre el número de semanas trabajadas",
				"observations": {
					"id": "KM x Semana",
					"measure": "km",
					"unit": {
						"name": "km"
						}
					}
				}
			}
		}
	]
