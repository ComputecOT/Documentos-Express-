# Generacion de documentos (v.1.0.0)

Este objeto JSON describe la configuración y composición de documentos para la generacion de campañas.

## Cracteristicas generales

- Estructura generica para documentos personalizados.
- Alta tasa de configuracion.
- Uso de interpolacion para informacion y configuraciones.

## Tipos de de documentos

- Cartas
    - Sencillas
    - Detalles.

## Estructura generica (JSON )

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
</table>

------------------------

### `document_composition`

| Campo                         | Descripción                                   |
|-------------------------------|-----------------------------------------------|
| `url_background`              | URL de la imagen de fondo.                   |
| `url_logo`                    | URL del logotipo.                            |
| `date`                        | Información de la fecha.                     |
| `date.title`                  | Título de la fecha (e.g., "Bogotá,").        |
| `date.value`                  | Valor de la fecha.                           |
| `window`                      | Información de la ventana del documento.     |
| `window.greeting`             | Información del saludo.                      |
| `window.greeting.title`       | Título del saludo (e.g., "Estimado(a)").     |
| `window.greeting.value`       | Valor del saludo con marcador de posición (e.g., `{{nombre}}`). |
| `window.direction`            | Información de la dirección.                 |
| `window.direction.title`      | Título de la dirección.                      |
| `window.direction.value`      | Valor de la dirección con marcador de posición (e.g., `{{direccion}}`). |
| `window.locale`               | Información de la localidad.                 |
| `window.locale.title`         | Título de la localidad.                      |
| `window.locale.value`         | Valor de la localidad.                       |
| `subject`                     | Información del asunto.                      |
| `subject.title`               | Título del asunto (e.g., "Asunto: ").        |
| `subject.value`               | Valor del asunto.                            |
| `paragraphs`                  | Array de párrafos del documento.             |
| `signature`                   | Información de la firma.                     |
| `signature.title`             | Título de la firma (e.g., "Atentamente,").   |
| `signature.QR_value`          | Valor del código QR.                         |
| `signature.url_signature`     | URL de la imagen de la firma.                |
| `signature.signatory`         | Nombre del firmante.                         |
| `signature.description_signatory` | Descripción del firmante (e.g., cargo).    |