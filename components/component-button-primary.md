# Button/Primary (Componente oficial)

**Nombre EXACTO:** `Button/Primary`

⚠️ Usa exclusivamente este componente de la librería oficial. No generes variaciones no listadas ni alteres propiedades fijas. Usa sus tokens de color y espacio tal como vienen definidos (no los sobrescribas).

---

## Visual Map
![Button/Primary variants](https://raw.githubusercontent.com/uxttech/design-system-docs/refs/heads/main/images/Button/Primary.png)

---

## Vista general

Botón interactivo para ejecutar la **acción principal** de un contexto o pantalla, con máxima jerarquía visual.

**Diferencia técnica clave:**

- **Button/Primary**: Acción principal, fondo visible, máxima jerarquía, sin variantes de Type
- **Button/Secondary**: Acciones secundarias, 5 variantes de Type (base/darker/lighter/ghost/danger)
- **Button/Tertiary**: Sin fondo, SIEMPRE requiere icono, menor jerarquía
- **Button/Icon**: Solo icono obligatorio, forma circular/redondeada

---

## Opciones disponibles

**State** (estado de interactividad):

- `Default`: Estado normal, interactuable
- `Disabled`: Botón deshabilitado, gris claro, no clickeable

**Focus** (dimensión transversal de foco):

- `False`: Sin foco (estado normal)
- `True`: Con foco visible (borde azul 2px para navegación por teclado, WCAG 2.4.7)

⚠️ **Nota importante**: Focus es una dimensión transversal independiente que indica la interacción activa del teclado. Puede combinarse con State=Default pero NO con State=Disabled.

---

## Opciones configurables

**Text_case** (formato del texto):

- `UPPER`: Texto en mayúsculas (default, recomendado)
- `Sentence`: Texto en formato oración (primera letra mayúscula)

**<< Icon** (icono izquierdo):

- `True`: Muestra icono a la izquierda del texto
- `False`: Sin icono izquierdo (default)

**Item right >>** (icono derecho):

- `True`: Muestra icono o badge numérico a la derecha del texto
- `False`: Sin elemento derecho (default)

**Nota**: Los iconos son opcionales y transversales. Se usan para reforzar semánticamente la acción o indicar dirección.

---

## Configurable properties

- **<< Icon**: cambiar entre True/False
- **Item right >>**: cambiar entre True/False
- **State**: cambiar entre Default, Disabled
- **Focus**: cambiar entre False, True
- **Text_case**: cambiar entre UPPER, Sentence
- **Texto del botón**: cambiar label

---

## Fixed properties

- No modificar altura del botón
- No cambiar padding horizontal
- No alterar gap interno
- No modificar colores según interpretación propia
- No cambiar tipografía
- No cambiar border-radius
- No modificar tamaño de iconos
- No cambiar tracking del texto

---

## Cómo usar

**Regla de oro: Solo UN botón Primary visible por contexto/pantalla**

**Cuándo usar Button/Primary:**

- Acción principal más importante del contexto
- Ejemplo label: Guardar, Enviar, Confirmar, Comprar, Siguiente
- La acción que el usuario debe realizar con mayor prioridad

**Según iconos:**

- **<< Icon = True**: Icono a la izquierda
  - Uso: Acciones con dirección (← Volver, ← Anterior) cuando es la acción principal
  - Iconos semánticos que refuerzan el texto (🔍 Buscar, + Crear)

- **Item right >> = True**: Icono a la derecha
  - Uso: Acciones con dirección (Siguiente →, Continuar →)
  - Indicadores de expansión (Desplegar ↓)

- **<< Icon = True + Item right >> = True**: Iconos en ambos lados
  - Uso: Acciones con contexto bidireccional (← Carrusel →)
  - Uso RARO, evitar en la mayoría de casos

- **Sin iconos (ambos False)**: Solo texto
  - Uso: Acciones claras sin necesidad de refuerzo visual
  - Default para la mayoría de botones

**Estados interactivos:**

- **Default**: Estado normal, cursor pointer
- **Focus**: Borde azul 2px visible (navegación por teclado, WCAG 2.4.7)
- **Disabled**: Gris claro, cursor not-allowed, no responde a hover/click

**Text_case:**

- **UPPER** (default): Texto en mayúsculas (ej: "GUARDAR")
  - Uso: Recomendado para la mayoría de botones
  - Da consistencia y diferenciación visual
- **Sentence**: Primera letra mayúscula (ej: "Guardar")
  - Uso: Contextos menos formales o cuando se requiere tono más conversacional

---

## Ejemplos

**Primary simple:**

```
State: Default
Focus: False
Label: "GUARDAR"
```

**Botón con foco activo (navegación por teclado):**

```
State: Default
Focus: True
Label: "CONFIRMAR"
→ Uso: Usuario navegando con teclado
```

**Botón Primary con icono izquierdo:**

```
State: Default
Focus: False
<< Icon: True
Label: "CREAR NUEVO"
```

**Botón deshabilitado:**

```
State: Disabled
Focus: False
Label: "GUARDAR"
→ Nota: Focus NO puede ser True cuando State=Disabled
```

**Botón Primary con dirección (Item right >>):**

```
State: Default
Focus: False
Item right >>: True
Label: "SIGUIENTE"
```

**Grupo de botones (Primary + Secondary):**

```
Button 1:
  Componente: Button/Secondary
  Type: base color
  State: Default
  Focus: False
  Label: "CANCELAR"

Button 2:
  Componente: Button/Primary
  State: Default
  Focus: False
  Label: "CONFIRMAR"

→ Resultado: Dos botones lado a lado, Secondary a la izquierda, Primary a la derecha
→ Uso: Confirmación de acción con opción de cancelar
```

---

## lo que la IA NUNCA debe hacer en ningún caso

❌ Inventar variantes  
❌ Más de un Primary por pantalla/contexto  
❌ Dibujar botón desde cero  
❌ Cambiar tamaños, colores o radius  
❌ Alterar tipografía  
❌ Cambiar tamaño de iconos  
❌ Usar iconos en ambos lados sin motivo

---

## Accesibilidad (para humanos, IA puede ignorar este apartado)

### WCAG 2.1.1 Keyboard

- Botones deben ser completamente accesibles por teclado
- **Tab**: Navegar entre botones
- **Enter/Space**: Activar botón enfocado

### WCAG 2.4.7 Focus Visible

- Focus ring visible obligatorio (2px azul)
- Contraste mínimo 3:1 con fondo
- No solo color para indicar focus

### WCAG 3.2.4 Consistent Identification

- Botones con misma función deben tener mismo label
- Ejemplo: "GUARDAR" debe ser consistente en toda la aplicación
- Iconos deben usarse de forma consistente (← Volver, Siguiente →)

### WCAG 4.1.2 Name, Role, Value

- Usar `<button>` nativo o `role="button"`
- `aria-label` si el botón solo tiene icono sin texto
- `aria-disabled="true"` para botones deshabilitados
- `type="button"` (default) | `type="submit"` (formularios)

### Navegación por teclado

1. **Tab**: Mover focus al siguiente botón
2. **Shift + Tab**: Mover focus al botón anterior
3. **Enter**: Activar botón enfocado
4. **Space**: Activar botón enfocado (alternativa a Enter)

### ARIA attributes recomendados

- `role="button"`: Si no se usa `<button>` nativo (NO recomendado)
- `aria-label`: Label descriptivo si el botón solo tiene icono
- `aria-describedby`: Asociar con texto de ayuda o advertencia
- `aria-disabled`: true para botones deshabilitados (además de disabled)
- `aria-pressed`: true/false para botones toggle (caso especial)
- `aria-hidden="true"`: Para iconos decorativos (SVG)

### Recomendaciones

- **Click area**: Todo el botón debe ser clickeable
- **Focus visible**: Contraste 3:1 con fondo, claramente distinguible
- **Hover vs Focus**: Diferenciar visualmente hover (mouse) de focus (teclado)
- **Disabled**: No usar solo color, incluir cursor not-allowed
- **Loading state**: Añadir aria-busy="true" durante carga
- **Consistencia**: Mismo label para misma acción en toda la app
- **Iconos**: aria-hidden="true" si son decorativos (texto ya describe acción)
- **Solo icono**: Requiere aria-label descriptivo obligatoriamente

### Jerarquía de botones

**Un solo Primary por contexto:**

- Solo el botón de acción principal debe ser Primary
- Resto de botones deben ser Secondary (con sus variantes)
- Ejemplo: "GUARDAR" (Primary) + "CANCELAR" (Secondary)

**Ordenamiento recomendado:**

- Desktop: Secondary izquierda, Primary derecha
- Mobile: Primary arriba (más accesible), Secondary abajo

**Espaciado entre botones:**

- Gap horizontal: 12px (`Size/spacing/layout-xs-2`)
- Gap vertical (mobile): 12px (`Size/spacing/layout-xs-2`)

### Loading state

- Cambiar label a estado de carga ("GUARDANDO...", "ENVIANDO...")
- Añadir spinner animado
- Deshabilitar botón (disabled + aria-disabled="true")
- Añadir aria-busy="true"
- No permitir múltiples clics

---

## Variant Signature (Figma)

Copy this signature with the chosen values:

`Button/Primary / {State} / {Focus} / {Text_case} / {<< Icon} / {Item right >>}`

| State    | Focus | Text_case | << Icon | Item right >> |
|----------|-------|-----------|---------|---------------|
| Default  | False | UPPER     | False   | False         |
| Disabled | True  | Sentence  | True    | True          |

Examples:
✅ Button/Primary / Default / False / UPPER / False / False
✅ Button/Primary / Default / True / UPPER / True / False
❌ Button/Primary / default / false / upper / false / false  ← case sensitive
❌ Button/Primary / Disabled / True / UPPER / False / False  ← Focus=True incompatible con Disabled

## Figma Binding
- **Nombre en librería**: `Button/Primary`
- **Separador**: ` / ` (con espacios)
- **Valores**: exact match, case sensitive
- **Regla**: especificar SIEMPRE las 5 propiedades, nunca asumir defaults

---

**Versión**: 2.0  
**Última actualización**: 2025-12-13
