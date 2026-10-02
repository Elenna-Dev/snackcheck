

## REGISTRO DE PRUEBAS




| Código| Tipo | Input | Resultado esperado | Status |
| --- | --- | --- | --- | --- |

| TC-F01 | Funcional | Código válido con ambos datos de nutrientes y Nutri-Score A/B | Veredicto en texto plano devuelto como saludable, al clasificarse tanto nutrientes como Nutri-Score como saludables | Aprobado |

| TC-F02 | Funcional | Código válido con 1 nutriente alto o  Nutri-Score C | Veredicto en texto plano devuelto como moderado, al primar el peor resultado. | Aprobado |

| TC-F03- | Funcional | Código válido con 2 o 3 nutrientes altos o  Nutri-Score D/E  | Veredicto en texto plano devuelto como no saludable, al primar el peor resultado. | Aprobado |



| TC-I01 | Integración | Código válido enviado a la API de Open Food Facts | HTTP 200 and API status: 1  | Aprobado |

| TC-I02 | Integración | Código desconocido enviado a la API de Open Food Facts | HTTP 404 and API status: 0  | Aprobado |



| TC-E01 | Error | Código de barras inexistente o vacío |  Error: 404 - Código de barras necesarios | Aprobado |

| TC-E02 | Error | Código de barras inválido |  Error: 404 - Código de barras no encontrado | Aprobado |

| TC-E03 | Error | Producto existente sin input de nutrientes | Error: 400 - Datos insuficientes | Aprobado  |



| TC-P01 | Rendimiento | Tiempo de ejecución del flujo completo de validación por código de barras | El proceso completo finaliza en menos de 1,5 segundos | Aprobado |
