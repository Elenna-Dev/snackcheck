#  Validador de Productos y Saludabilidad con n8n

Este es un flujo de trabajo que he creado en la herramienta n8n para consultar productos mediante su código de barras, analizar su información nutricional y generar un veredicto claro sobre qué tan saludables son.

---

## Propósito
El objetivo de este proyecto es automatizar la evaluación nutricional de un producto. A partir de un código de barras, el flujo busca los datos del alimento, revisa sus nutrientes (grasas, azúcar y sal) y su Nutri-Score, y construye un resumen fácil de entender para el consumidor con marcadores de colores.

---

## Cómo funciona
El flujo sigue estos pasos básicos:

1. **Entrada de datos:** Recibe el código de barras del producto mediante un Webhook.
2. **Validación:** Comprueba que el código de barras sea válido (que contenga solo números).
3. **Consulta de información:** Conecta con la API pública de Open Food Facts para traer los datos reales del producto.
4. **Clasificación y cálculo:** 
   - Un nodo revisa si el Nutri-Score o los valores de azúcar, grasa y sal superan ciertos límites.
   - Un nodo de código asigna una puntuación numérica (0 para saludable, 1 para moderado, 3 para no saludable) manteniendo los datos originales.
5. **Veredicto final:** Une toda la información en un formato de texto amigable con emojis (🟢, 🟡, 🔴) para mostrar el resultado.

---

##  Configuración
Para poner en marcha este flujo en tu propia cuenta de n8n:

1. Descarga o copia el archivo JSON del flujo.
2. En tu panel de n8n, crea un nuevo flujo y selecciona **Import from File** (o pega el JSON).
4. Activa el flujo o ejecútalo en modo de prueba.

---

## Uso
1. Envía una petición al nodo inicial con el código de barras que quieras consultar.
2. El flujo procesará la solicitud automáticamente.
3. En el nodo final (Respond tu Weebhook), obtendrás un campo llamado "veredicto" con un resumen como este:

   > **Veredicto: Producto No Saludable**
   > 
   > **Valores Nutricionales (por 100g):**
   > - 🟢 Grasas: 0g
   > - 🔴 Azúcar: 10.6g
   > - 🟢 Sal: 0g

---

## Manejo de errores
- **Código de barras no válido:** Si la entrada contiene letras o caracteres extraños, el nodo de validación corta el proceso para evitar llamadas innecesarias.
- **Producto no encontrado:** Si la API de Open Food Facts no tiene registrado el código de barras, se captura la respuesta para evitar que el flujo falle bruscamente.
- **Valores por defecto:** En la lógica del nodo Code, si la clasificación no encaja exactamente con "Saludable" o "Moderado", se le asigna por seguridad la puntuación máxima de precaución (3 - No Saludable).

---

## Limitaciones
- **Dependencia externa:** Si la API de Open Food Facts falla o está caída, el flujo no podrá obtener información.
- **Productos incompletos:** Si un producto no tiene registrados los datos de azúcar, sal o grasa en la base de datos pública, la evaluación de ese nutriente se mostrará con valores en 0 por defecto.
- **Reglas fijas:** Los límites de nutrientes (por ejemplo, azúcar > 22.5g o sal > 1.5g) están definidos de forma rígida y no cambian según la categoría del alimento.