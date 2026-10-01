

## REGISTRO DE PRUEBAS
\
\
#\
\
| C\'f3digo| Tipo | Input | Resultado esperado | Status |\
| --- | --- | --- | --- | --- |\
\
| TC-F01 | Funcional | C\'f3digo v\'e1lido con ambos datos de nutrientes y Nutri-Score A/B | Veredicto en texto plano devuelto como saludable, al clasificarse tanto nutrientes como Nutri-Score como saludables | Aprobado |\
\
| TC-F02 | Funcional | C\'f3digo v\'e1lido con 1 nutriente alto o  Nutri-Score C | Veredicto en texto plano devuelto como moderado, al primar el peor resultado. | Aprobado |\
\
| TC-F03- | Funcional | C\'f3digo v\'e1lido con 2 o 3 nutrientes altos o  Nutri-Score D/E  | Veredicto en texto plano devuelto como no saludable, al primar el peor resultado. | Aprobado |\
\
\
\
| TC-I01 | Integraci\'f3n | C\'f3digo v\'e1lido enviado a la API de Open Food Facts | HTTP 200 and API status: 1  | Aprobado |\
\
| TC-I02 | Integraci\'f3n | C\'f3digo desconocido enviado a la API de Open Food Facts | HTTP 404 and API status: 0  | Aprobado |\
\
\
\
| TC-E01 | Error | C\'f3digo de barras inexistente o vac\'edo |  Error: 404 - C\'f3digo de barras necesarios |\'a0Aprobado |\
\
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0
\cf0 | TC-E02 | Error | C\'f3digo de barras inv\'e1lido |  Error: 404 - C\'f3digo de barras no encontrado | Aprobado |\
\
| TC-E03 | Error | Producto existente sin input de nutrientes | Error: 400 - Datos insuficientes | Aprobado  |\
\
\
\
| TC-P01 | Rendimiento | \expnd0\expndtw0\kerning0
\outl0\strokewidth0 \strokec2 Tiempo de ejecuci\'f3n del flujo completo de validaci\'f3n por c\'f3digo de barras | El proceso completo finaliza en menos de 1,5 segundos | Aprobado |}
