# Informe Técnico de Implementación: Portal Dirección Académica
## Adaptación del Wireframe y Especificación Funcional al Ecosistema Joomla de la UNAL Sede Medellín

**Proyecto:** Nuevo Portal Web de la Dirección Académica  
**Entorno Tecnológico:** CMS Joomla (Plantilla Institucional Sede Medellín · `sede.css`)  
**Insumos Base:** 
1. `Guía Pag.Web.docx` (*Guía Técnica de Desarrollo y Especificación de Contenidos: Portal Dirección Académica*)
2. `wireframe dirección académica.pdf` (*Mockup de 6 vistas diseñado en Adobe Illustrator*)
3. Capturas oficiales del Header y Home UNAL Sede Medellín (Header gris con subdominio, públicos, buscador, escudo, banner rotativo y botones de colores institucionales)
4. Directrices Generales de Entorno y Sistema de Diseño Unimedios (`articulos-sede-medellin/system-design/` y `GEMINI.md`)

---

## 1. Resumen Ejecutivo y Alcance

El presente informe establece la formulación técnica, visual y arquitectónica de cómo quedará implementado el contenido de la **Dirección Académica** en el CMS Joomla de la Universidad Nacional de Colombia - Sede Medellín.

A solicitud técnica, se definen y modelan **dos (2) escenarios de implementación**:
- **Escenario 1 (Página Web Completa):** Subsitio Joomla independiente (ej. `academica.medellin.unal.edu.co`) con header institucional propio, banner rotativo grande en Home y barra inferior de botones con los colores institucionales de la sede.
- **Escenario 2 (Artículos Joomla):** Integración como artículos institucionales (`com_content`) dentro del portal principal `medellin.unal.edu.co`, utilizando la cabecera `.bo-banner` y navegación Sticky Quicknav sin colisionar con el menú global de la sede.

Ambas alternativas resuelven las directrices obligatorias de la Sede: **ancho 100% full-width**, no duplicar calendarios de Registro y Matrícula, estandarización de canales de contacto hacia **Punto de Contacto** y ajuste de nómina institucional.

---

## 2. El Header Institucional Oficial (Común a Todas las Webs UNAL)

Tal como se evidencia en las páginas de la Sede Medellín, el encabezado oficial se compone de:
1. **Bloque Escudo UNAL:** Caja gris oscura (`#3A3A3A`) a la izquierda con el escudo oficial de la Universidad Nacional en blanco.
2. **Barra Superior Institucional:** Franja gris intermedia (`#505050` / `#555555`) que incluye:
   - Identificador de ubicación / subdominio (ej. `📍 academica.medellin.unal.edu.co` o `medellin.unal.edu.co`).
   - Accesos a públicos institucionales: `Aspirantes | Estudiantes | Egresados | Docentes | Administrativos`.
   - Botón destacado permanente: `Moodle LMS (UN Virtual) ↗`.
3. **Escudo de Colombia:** Escudo oficial de la República en formato circular sobre la derecha.
4. **Menú Horizontal Institucional:** Barra gris (`#444444`) con línea inferior de acento institucional en cyan/verde teal (`#00A48A`). En el extremo derecho integra el buscador rápido con lupa.

---

## 3. Escenario 1: Implementación como Página Web Completa (Portal Propio)

Aplica si la Dirección Académica cuenta con su propia instalación o subsitio en Joomla bajo un subdominio institucional (ej. `academica.medellin.unal.edu.co`).

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ [HEADER OFICIAL UNAL]: Escudo UNAL + academica.medellin.unal.edu.co + Públicos + Moodle│
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [MENÚ DE LA DEPENDENCIA]: Inicio | Quiénes Somos | Estudiantes | Docentes | Convenios  │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [BANNER ROTATIVO GRANDE - HERO SLIDER 100% ANCHO]:                                     │
│ Fotografía panorámica del Campus El Volador + Titular conmemorativo                    │
│ "Dirección Académica · Sede Medellín / Acompañamos tu formación integral"              │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [BARRA DE BOTONES CON COLORES INSTITUCIONALES (Debajo del Banner)]:                    │
│ ┌───────────────┬────────────────┬───────────────┬───────────────┬──────────────────┐ │
│ │ Punto de      │ Calendarios    │ Tutorías y    │ Cursos de     │ Convocatorias    │ │
│ │ Contacto      │ Académicos     │ Grupos GEA    │ Idiomas       │ e Innovación     │ │
│ │ (#024060 Azul)│ (#00A48A Cyan) │ (#00966C Teal)│ (#06132D Noche│ (#9AB147 Oliva)  │ │
│ └───────────────┴────────────────┴───────────────┴───────────────┴──────────────────┘ │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [CUERPO DEL HOME]:                                                                     │
│ ├── Noticias y novedades académicas (com_content)                                      │
│ ├── Sidebar: Aviso institucional y enlace directo al calendario de Registro            │
│ ├── Módulos Transversales: 5.0 Evaluación Docente | 6.0 Acreditación | 7.0 Programación│
│ └── Módulo Inferior: Punto de Contacto (Atención y tickets)                            │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [FOOTER INSTITUCIONAL]: Bloque 42 Piso 2 · Redes, Enlaces Legales y Copyright          │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

### Características Técnicas del Escenario 1:
- **Banner Rotativo:** Módulo tipo slider con imágenes en formato WebP optimizadas y textos ocupando el 100% del ancho sin cortes forzados (`width: 100% !important; max-width: 100% !important;`).
- **Botones Institucionales:** Reproduce exactamente la botonera destacada del Home institucional de la sede, utilizando la paleta pentacromática aprobada:
  1. *Azul Institucional (`#024060`):* Punto de Contacto.
  2. *Cyan / Turquesa (`#00A48A`):* Calendarios Académicos (conduce a Registro).
  3. *Verde Esmeralda (`#00966C`):* Tutorías y Grupos GEA.
  4. *Azul Noche Profundo (`#06132D`):* Cursos de Idiomas de Libre Elección.
  5. *Verde Oliva Institucional (`#9AB147`):* Convocatorias e Innovación Docente.

---

## 4. Escenario 2: Implementación como Artículos Joomla (Dentro del Portal Principal de la Sede)

Aplica si la Dirección Académica se publica dentro del portal central `medellin.unal.edu.co` (por ejemplo en `medellin.unal.edu.co/la-sede/direccion-academica`).

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ [HEADER Y MENÚ GLOBAL DEL PORTAL SEDE]:                                                │
│ medellin.unal.edu.co | LA SEDE | ESTUDIAR EN LA UNAL | FACULTADES | INVESTIGACIÓN...   │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [CONTENIDO DEL ARTÍCULO JOOMLA (com_content)]:                                         │
│                                                                                        │
│ 1. BANNER INSTITUCIONAL DE CABECERA (.bo-banner):                                      │
│    Fotografía del campus con filtro institucional y titular de la dependencia.         │
│                                                                                        │
│ 2. MENÚ STICKY EN PÁGINA (QUICKNAV ACCESIBLE):                                         │
│    [1. ¿Quiénes Somos?] [2. Estudiantes] [3. Docentes] [4. Convenios] [5. Contacto]    │
│                                                                                        │
│ 3. SECCIÓN 1: ¿QUIÉNES SOMOS? Y MARCO NORMATIVO:                                       │
│    Misión, Visión, Funciones en acordeón (.unal-accordion) y directorio actualizado.   │
│                                                                                        │
│ 4. SECCIÓN 2: SERVICIOS PARA ESTUDIANTES:                                              │
│    Saber Pro, Movilidad intersedes, GEA, Idiomas y 2 infografías de solicitudes.       │
│                                                                                        │
│ 5. SECCIÓN 3: SERVICIOS PARA DOCENTES:                                                 │
│    Gestión Curricular, microcurrículos, Reflexión Curricular e Innovación Académica.   │
│                                                                                        │
│ 6. SECCIÓN 4: CONVENIOS INTERINSTITUCIONALES:                                          │
│    Tabla accesible (.unal-table) y matriz de descargas en PDF.                         │
│                                                                                        │
│ 7. SECCIÓN 5: ATENCIÓN Y CONTACTO:                                                     │
│    Botón destacado hacia el sistema de tickets de Punto de Contacto.                   │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [FOOTER GLOBAL DE LA SEDE MEDELLÍN]                                                    │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

### Características Técnicas del Escenario 2:
- **No duplicación de menús:** No se monta un menú de primer nivel que compita con el menú general de la sede.
- **Navegación Sticky Quicknav:** Incorpora una barra fija horizontal con chips accesibles (`.quicknav-link`) que acompaña el desplazamiento del usuario por las distintas secciones sin recargar la página.
- **Mantenimiento Ultraligero:** Todo el contenido se administra en artículos estándar de Joomla (`com_content`), beneficiándose de las más de 11.000 líneas de estilos nativos de `sede.css` sin necesidad de CSS externo ni scripts complejos.

---

## 5. Tabla Comparativa de Ambos Escenarios

| Parámetro | Escenario 1: Página Web Completa | Escenario 2: Artículos en Portal Sede |
|---|---|---|
| **URL / Acceso** | `academica.medellin.unal.edu.co` | `medellin.unal.edu.co/la-sede/direccion-academica` |
| **Header** | Header UNAL con dominio propio y menú de la dependencia. | Header UNAL con menú general institucional de la sede. |
| **Cabecera en Home** | **Banner rotativo grande (hero slider) + 5 botones de colores institucionales**. | **Banner de oficina institucional (.bo-banner) + Quicknav Sticky**. |
| **Gestión Técnica** | Requiere configuración de plantilla, módulos, menús y permisos en Joomla. | Se edita directamente en el gestor de artículos de Joomla. |
| **Navegación Interna** | Menú superior con páginas y subpáginas separadas. | Navegación dentro del artículo con ScrollSpy / pestañas. |
| **Tiempo de Salida** | Mayor (requiere aprovisionamiento y pruebas de sitio). | Inmediato (maquetación directa sobre la plantilla actual). |

---

## 6. Prototipo Interactivo Disponible

Se ha desarrollado un prototipo funcional interactivo en un único archivo:
👉 **[prototipo-direccion-academica.html](file:///home/sara/Documents/unimedios/direccion-academica/prototipo-direccion-academica.html)**

El archivo cuenta con un selector en la barra superior que permite conmutar en tiempo real entre:
1. `🌐 Versión 1: Como Página Web Completa` (con el banner rotativo y la botonera institucional).
2. `📄 Versión 2: Como Artículos Joomla` (con el banner de oficina y la barra Quicknav Sticky).
