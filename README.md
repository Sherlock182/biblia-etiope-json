# La Biblia Etíope en JSON

La Biblia Etíope completa en español, en un solo archivo JSON: los **88 libros** del canon etíope, ordenados por libro, capítulo y versículo, y agrupados en Antiguo Testamento, Nuevo Testamento y Libros apócrifos.

Es el mismo texto que usa la app [Biblioteca Digital](https://github.com/Sherlock182/Biblioteca-Digital), ya corregido:

- Las fechas aparecen de forma sencilla, por ejemplo *(año 1429)*.
- Se quitaron los símbolos « », [ ], < >, { } y †.
- Se corrigieron errores de traducción.
- 1, 2 y 3 Meqabyan se tradujeron de nuevo desde el original.

| | Libros | Capítulos | Versículos |
|---|---:|---:|---:|
| Antiguo Testamento | 39 | 929 | 23 029 |
| Nuevo Testamento | 27 | 260 | 7 883 |
| Libros apócrifos | 22 | 513 | 8 974 |
| **Total** | **88** | **1 702** | **39 886** |

## Archivos

| Archivo | Para qué sirve |
|---|---|
| [`biblia-etiope.json`](biblia-etiope.json) | Con sangría, fácil de leer y revisar (8.9 MB) |
| [`biblia-etiope.min.json`](biblia-etiope.min.json) | Compacto, para usar en apps y páginas web (6.4 MB) |

## Estructura

```json
{
  "titulo": "La Biblia Etíope",
  "idioma": "es",
  "libros_total": 88,
  "capitulos_total": 1702,
  "versiculos_total": 39886,
  "libros": [
    {
      "numero": 1,
      "nombre": "Génesis",
      "clave": "Genesis",
      "testamento": "Antiguo Testamento",
      "grupo": "Pentateuco (La Ley)",
      "capitulos": [
        {
          "capitulo": 1,
          "versiculos": [
            { "versiculo": 1, "texto": "En el principio, Dios creó los cielos y la tierra." }
          ]
        }
      ]
    }
  ]
}
```

Campos que aparecen solo en algunos versículos:

- **`hasta`**: aparece cuando el texto abarca varios versículos. Por ejemplo, `{ "versiculo": 3, "hasta": 4, ... }` es el texto de los versículos 3 y 4.
- **`titulos`**: son los títulos que van antes del versículo. Cada uno tiene un `tipo`:
  - `titulo`: el encabezado de una sección.
  - `inscripcion`: la línea que va al inicio de un salmo, como "Salmo de David".
  - `division`: una división mayor, como "Libro 1" en Salmos.

## Ejemplo de uso

```js
const biblia = require('./biblia-etiope.json');

const libro = biblia.libros.find(l => l.nombre === 'Enoc');
const versiculo = libro.capitulos[0].versiculos[0];
console.log(`Enoc 1:${versiculo.versiculo} ${versiculo.texto}`);
```

```python
import json

with open('biblia-etiope.json', encoding='utf-8') as f:
    biblia = json.load(f)

for libro in biblia['libros']:
    if libro['testamento'] == 'Libros apócrifos':
        print(libro['nombre'], len(libro['capitulos']), 'capítulos')
```

## Libros

**Antiguo Testamento (39):** Génesis, Éxodo, Levítico, Números, Deuteronomio, Josué, Jueces, Rut, 1 y 2 Samuel, 1 y 2 Reyes, 1 y 2 Crónicas, Esdras, Nehemías, Ester, Job, Salmos, Proverbios, Eclesiastés, Cantares, Isaías, Jeremías, Lamentaciones, Ezequiel, Daniel, Oseas, Joel, Amós, Abdías, Jonás, Miqueas, Nahúm, Habacuc, Sofonías, Hageo, Zacarías y Malaquías.

**Nuevo Testamento (27):** Mateo, Marcos, Lucas, Juan, Hechos, Romanos, 1 y 2 Corintios, Gálatas, Efesios, Filipenses, Colosenses, 1 y 2 Tesalonicenses, 1 y 2 Timoteo, Tito, Filemón, Hebreos, Santiago, 1 y 2 Pedro, 1, 2 y 3 Juan, Judas y Apocalipsis.

**Libros apócrifos (22):** 1 Esdras (Ezra Kali), Tobías, Judit, Adiciones a Ester, 1, 2 y 3 Meqabyan, Oración de Manasés, Salmo 151, Sabiduría de Salomón, Eclesiástico (Sirácides), Baruc, Carta de Jeremías, 4 Baruc, Cántico de los tres jóvenes, Susana, Bel y el dragón, Jubileos, Enoc, 2 Enoc, 2 Esdras (Ezra Sutuel) y 1 Clemente.

---

Desarrollado por **Ingeniero Oseas Nahun Montalvo Rogel** · [4603642023@mail.utec.edu.sv](mailto:4603642023@mail.utec.edu.sv) · [GitHub](https://github.com/Sherlock182)
