# Resumen Ejecutivo: Implementación Web Dirección Académica
**Para:** Equipo Directivo y Comité Web · Dirección Académica / Unimedios  
**Objetivo:** Comparativa de las dos (2) vías de implementación en Joomla y decisiones clave  
**Tiempo estimado de lectura:** 2 minutos  

---

### 1. El Header Oficial Institucional (Todas las Webs UNAL)
Todas las páginas web de la Universidad Nacional de Colombia cuentan con el **encabezado institucional gris oficial** (escudo nacional y de la sede, barra de públicos `Aspirantes | Estudiantes | Egresados | Docentes | Administrativos`, buscador y acceso permanente a `Moodle LMS / UN Virtual`).

A partir de este marco, existen **dos (2) formas oficiales de implementar la Dirección Académica en Joomla**:

---

### 2. Las Dos Vías de Implementación Técnica en Joomla

```
┌────────────────────────────────────────────────────────────────────────────────────────────────┐
│ OPCIÓN 1: COMO PÁGINA WEB COMPLETA (PORTAL PROPIO)                                            │
│ (Ej. subdominio academica.medellin.unal.edu.co)                                                │
├────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. Header Oficial UNAL completo con el subdominio de la dependencia.                          │
│ 2. Menú de navegación propio (Quiénes Somos | Estudiantes | Docentes | Convenios).             │
│ 3. En el Home:                                                                                 │
│    - Banner rotativo grande (hero slider) con fotos del campus y logo conmemorativo.           │
│    - Fila de 5 botones institucionales con sus colores oficiales:                              │
│      [Punto de Contacto (Azul)]  [Calendarios (Cyan)]  [Grupos GEA (Verde)]                    │
│      [Cursos Idiomas (Azul Noche)]  [Convocatorias (Verde Oliva)]                              │
│    - Cuerpo del sitio: Noticias, módulos transversales de evaluación y acreditación.           │
├────────────────────────────────────────────────────────────────────────────────────────────────┤
│ OPCIÓN 2: COMO ARTÍCULOS JOOMLA (DENTRO DEL PORTAL PRINCIPAL)                                  │
│ (Ej. sección dentro de medellin.unal.edu.co/la-sede/direccion-academica)                       │
├────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. El Header y Menú Global pertenecen al portal de la Sede Medellín (LA SEDE | FACULTADES...). │
│ 2. La dependencia se publica mediante el componente de artículos (com_content).                │
│ 3. Estructura interna del artículo:                                                            │
│    - Banner de cabecera de oficina (.bo-banner institucional de 100% ancho).                   │
│    - Menú Sticky Quicknav (chips/pestañas accesibles) para navegar sin recargar la página:      │
│      [1. Quiénes Somos] [2. Estudiantes] [3. Docentes] [4. Convenios] [5. Contacto]           │
│    - Bloques temáticos limpios con tarjetas, tablas de convenios y acordeones (.sede.css).     │
└────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

### 3. Matriz de Decisión: ¿Cuál Elegir?

| Criterio | Opción 1: Página Web Completa (Portal Propio) | Opción 2: Artículos en el Portal Sede |
|---|---|---|
| **Estructura** | Subsitio independiente con su propio menú. | Sección integrada en la web central de la Sede. |
| **Cabecera Home** | **Banner rotativo grande + 5 botones de colores** (patrón oficial UNAL). | **Banner de oficina (.bo-banner) + Menú Sticky Quicknav**. |
| **Mantenimiento** | Requiere gestionar menús, módulos y permisos de portal propio en Joomla. | Muy ligero: se edita directamente como artículos de Joomla. |
| **Trámites / Fechas** | Botón de acceso directo al portal de Registro y Matrícula. | Enlaces directos a Registro sin duplicar resoluciones. |
| **Recomendado cuando...** | La dependencia requiere autonomía total de contenidos, publicaciones y subdominio. | Se busca una consulta directa y rápida dentro del árbol de la Sede sin dispersar sitios. |

---

### 4. Ajustes de Contenido que Aplican a Ambas Versiones
1. **Directorio Humano:** Aplicar actualización de nómina (incluir a Priscila; retirar a Fiorela y M) y mantener únicamente correos de proceso (sin correos personales `@unal.edu.co` ni extensiones directas).
2. **Cursos de Idiomas:** Incluir la nota aclaratoria de que la oferta electiva la ejecuta el Centro de Idiomas.
3. **Punto de Contacto:** Canalizar toda la radicación al sistema oficial de tickets.

> **Prototipo Interactivo en Vivo:**  
> Abra el archivo [prototipo-direccion-academica.html](file:///home/sara/Documents/unimedios/direccion-academica/prototipo-direccion-academica.html) en su navegador web. En la parte superior encontrará los botones para conmutar y comparar en tiempo real la **Versión 1 (Página Web)** y la **Versión 2 (Artículos)**.
