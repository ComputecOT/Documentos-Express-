# Generacion de documentos (v.1.0.0)

Este objeto JSON describe la configuración y composición de documentos para la generacion de campañas.

## Cracteristicas generales

- Estructura generica para documentos personalizados.
- Alta tasa de configuracion.
- Uso de interpolacion para informacion y configuraciones.

## Tipos de de documentos

- Cartas
    - Sencillas. <a href="./Estructuras/Cartas/Sencilla/Estructura_CS.xlsx" download="Estructura_CS.xlsx">Descargar estructura</a>
    - Detalles. <a href="./Estructuras/Cartas/Detalle/Estructura_CD.xlsx" download="Estructura_CD.xlsx">Descargar estructura</a>

** Es posible renombrar el archivo mas no alterar la estructura pre-establecida, se podran agregar N numero de variables a partir de la columna 9 (I).

## Interpolación

Todos los campos tanto para información como para configuracion, se encuentran habilitados para el uso de interpolacion, la cual conciste en generar cadenas de texto haciendo uso de las variables en los datos enviados para los registros:

```
    sintaxis: {{nombre_de_variable}}
```

#### Ejemplo:

- Se nombran los pdf's de salida con un texto fijo y la variable identificacion de cada registro.
- Se encriptan los pdf's con la variable identificacion. 

```
    "document_name": "texto_fijo_mas_variable_{{Numero de identificacion}}",
    "document_password": "{{Numero de identificacion}}",
```

- **Las variables deben existir y se deben referenciar con el mismo nombre enviado en el .xlsx**.

## Estructura general (JSON )

``` 
{
    "company_data": {
        "nit": "",
        "razon_social": "",
        "partner": {
            "nit": "",
            "razon_social": ""
        }
    },
    "type_document": "",
    "document_name": "",
    "document_password": "",
    "services": {
        "email": {
            "service": ,
            "sender": "",
            "mask": "",
            "subject": ""
        },
        "sms": {
            "service": ,
            "message": ""
        },
        "generatepdf": {
            "service": ,
            "transmission_direction": "",
            "user": "",
            "password": ""
        },
        "strorage": {
            "service": ,
            "time_storage": 
        },
        "print": {
            "service": ,
            "type_print": ""
        }
    },
    "document_composition": {
        "url_background": "",
        "url_logo": "",
        "colors": {
            "color_font": "",
            "color_fill_table_titles": "",
            "color_font_table_titles": ""
        },
        "title_document": "",
        "date": {
            "title": "",
            "value": ""
        },
        "window": {
            "greeting": {
                "title": "",
                "value": ""
            },
            "direction": {
                "title": "",
                "value": ""
            },
            "locale": {
                "title": "",
                "value": ""
            },
        },
        "subject": {
            "title": "",
            "value": ""
        },
        "paragraphs": [
            "",
            ""
        ],
        "signature": {
            "title": "",
            "url_signature": "",
            "signatory": "",
            "description_signatory": ""
        }
    }
}
```

## Descripcion

<table>
    <tr>
        <th>Campo</th>
        <th>Tipo</th>
        <th>Contenido</th>
        <th>Descripción</th>
    </tr>
    <tr>
        <td><code>company_data</code></td>
        <td>Object</td>
        <td>
            <table>
                <tr>
                    <td><code>nit</code></td>
                    <td>String</td>
                    <td>Nit de la compañia solicitante.</td>
                </tr>
                <tr>
                    <td><code>razon_social</code>
                    <td>String</td>
                    <td>Razon social de la compañia solicitante.</td>
                </tr>
                <tr>
                    <td><code>partner</code>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>nit</code></td>
                                <td>String</td>
                                <td>Nit de la compañia Aliada.</td>
                            </tr>
                            <tr>
                                <td><code>razon_social</code></td>
                                <td>String</td>
                                <td>Razon social de la compañia Aliada.</td>
                            </tr>
                        </table>
                    </td>
                </tr>
            </table>
        </td>
        <td>Datos de la compañia solicitante y Aliado.</td>
    </tr>
    <tr>
        <td><code>type_document</code></td>
        <td>String</td>
        <td></td>
        <td>Identificador del tipo de documento. (ej., "CS-0001")</td>
    </tr>
    <tr>
        <td><code>document_name</code></td>
        <td>String</td>
        <td></td>
        <td>Nombre del documento (ej., "{{num_identificacion}}_CS")</td>
    </tr>
    <tr>
        <td><code>document_password</code></td>
        <td>String</td>
        <td></td>
        <td>Contraseña del documento. (ej., "{{num_identificacion}}") </td>
    </tr>
    <tr>
        <td><code>services</code></td>
        <td>Object</td>
        <td>
            <table>
                <tr>
                    <td>
                        <code>email</code>
                    </td>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>service</code></td>
                                <td>Boolean</td>
                                <td>Aplica el servicio de correo.</td>
                            </tr>
                            <tr>
                                <td><code>sender</code></td>
                                <td>String</td>
                                <td>Dirección del remitente.</td>
                            </tr>
                            <tr>
                                <td><code>mask</code></td>
                                <td>String</td>
                                <td>Máscara del correo.</td>
                            </tr>
                            <tr>
                                <td><code>subject</code></td>
                                <td>String</td>
                                <td>Asunto del correo.</td>
                            </tr>
                        </table>
                    </td>
                </tr>
                <tr>
                    <td>
                        <code>sms</code>
                    </td>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>service</code></td>
                                <td>Boolean</td>
                                <td>Aplica el servicio de sms.</td>
                            </tr>
                            <tr>
                                <td><code>message</code></td>
                                <td>String</td>
                                <td>Mensaje para el SMS</td>
                            </tr>
                        </table>
                    </td>
                </tr>
                <tr>
                    <td>
                        <code>generatepdf</code>
                    </td>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>service</code></td>
                                <td>Boolean</td>
                                <td>Aplica el servicio de generación de PDF.</td>
                            </tr>
                            <tr>
                                <td><code>transmission_direction</code></td>
                                <td>String</td>
                                <td>Dirección de transmisión del PDF.</td>
                            </tr>
                            <tr>
                                <td><code>user</code></td>
                                <td>Boolean</td>
                                <td>Usuario del canal.</td>
                            </tr>
                            <tr>
                                <td><code>password</code></td>
                                <td>String</td>
                                <td>Contraseña del canal.</td>
                            </tr>
                        </table>
                    </td>
                </tr>
                <tr>
                    <td>
                        <code>storage</code>
                    </td>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>service</code></td>
                                <td>Boolean</td>
                                <td>Aplica el servicio de almacenamiento.</td>
                            </tr>
                            <tr>
                                <td><code>time_storage</code></td>
                                <td>Number</td>
                                <td>Tiempo de almacenamiento en días.</td>
                            </tr>
                        </table>
                    </td>
                </tr>
                <tr>
                    <td>
                        <code>print</code>
                    </td>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>service</code></td>
                                <td>Boolean</td>
                                <td>Aplica el servicio de impresión.</td>
                            </tr>
                            <tr>
                                <td><code>type_print</code></td>
                                <td>String</td>
                                <td>Tipo de impresión (S o D).</td>
                            </tr>
                        </table>
                    </td>
                </tr>
            </table>
        </td>
        <td>Datos de los servicios asociado a la campaña.</td>
    </tr>
    <tr>
        <td><code>document_composition</code></td>
        <td>Object</td>
        <td>
            <table>
               <tr>
                    <td><code>url_background</code></td>
                    <td>String</td>
                    <td>URL de la imagen de fondo.</td>
               </tr>
               <tr>
                    <td><code>url_logo</code></td>
                    <td>String</td>
                    <td>URL del logotipo.</td>
               </tr>
               <tr>
                    <td><code>date</code></td>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>title<code></td>
                                <td>String</td>
                                <td>Título de la fecha (e.g., "Bogotá,").</td>
                            </tr>
                            <tr>
                                <td><code>value<code></td>
                                <td>String</td>
                                <td>Valor de la fecha. </td>
                            </tr>
                        </table>
                    </td>
               </tr>
               <tr>
                    <td><code>window</code></td>
                    <td>Object</td>
                    <td>
                        <table>
                            <tr>
                                <td><code>greeting</code></td>
                                <td>Object</td>
                                <td>
                                     <table>
                                        <tr>
                                            <td><code>title</code></td>
                                            <td>String</td>
                                            <td>Título del saludo (e.g., "Estimado(a)").</td>
                                        </tr>
                                        <tr>
                                            <td><code>value</code></td>
                                            <td>String</td>
                                            <td>Saludo.</td>
                                        </tr>
                                    </table>
                                </td>
                            </tr>
                            <tr>
                                 <td><code>direction</code></td>
                                 <td>Object</td>
                                 <td>
                                     <table>
                                        <tr>
                                            <td><code>title</code></td>
                                            <td>String</td>
                                            <td>Título de la dirección.</td>
                                        </tr>
                                        <tr>
                                            <td><code>value</code></td>
                                            <td>String</td>
                                            <td>Valor de la dirección.</td>
                                        </tr>
                                    </table>
                                 </td>
                            </tr>
                            <tr>
                                 <td><code>locale</code></td>
                                 <td>Object</td>
                                 <td>
                                     <table>
                                        <tr>
                                            <td><code>title</code></td>
                                            <td>String</td>
                                            <td>Título de la ubicación.</td>
                                        </tr>
                                        <tr>
                                            <td><code>value</code></td>
                                            <td>String</td>
                                            <td>Valor de ubicación.</td>
                                        </tr>
                                    </table>
                                 </td>
                            </tr>
                        </table>
                    </td>
               </tr>
               <tr>
                    <td><code>subject</code></td>
                    <td>Object</td>
                    <td>
                        <table>
                        <tr>
                            <td><code>title</code></td>
                            <td>String</td>
                            <td>Título del asunto (e.g., "Asun").</td>
                        </tr>
                        <tr>
                            <td><code>value</code></td>
                            <td>String</td>
                            <td>Valor del asunto.</td>
                        </tr>
                    </table>
                    </td>
                </tr>
               <tr>
                    <td><code>paragraphs</code></td>
                    <td>String[]</td>
                    <td>Array de párrafos del documento.</td>
               </tr>
               <tr>
                    <td><code>signature</code></td>
                    <td>Object</td>
                    <td>
                        <table>
                             <tr>
                                 <td><code>title</code></td>
                                 <td>String</td>
                                 <td>Título de la firma (e.g., "Atentamente,").</td>
                             </tr>
                             <tr>
                                 <td><code>url_signature</code></td>
                                 <td>String</td>
                                 <td>URL de la imagen de la firma.</td>
                             </tr>
                             <tr>
                                 <td><code>signatory</code></td>
                                 <td>String</td>
                                 <td>Nombre del firmante.</td>
                             </tr>
                             <tr>
                                 <td><code>description_signatory</code></td>
                                 <td></td>
                                 <td>Descripción del firmante (e.g., cargo).</td>
                             </tr>
                        </table>
                    </td>
               </tr>               
            </table>
        </td>
        <td>Composición del documento.</td>
    </tr>
</table>