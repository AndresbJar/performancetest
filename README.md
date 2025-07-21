# Prueba de Performance con JMeter – Login API 

Este README documenta el proceso de ejecución de una prueba de carga con **Apache JMeter**, simulando peticiones al endpoint de login de la API `https://fakestoreapi.com/auth/login`. El objetivo fue cumplir los criterios establecidos validando la capacidad de respuesta del sistema bajo carga.

---

## Objetivos

- ✅ Obtener al menos **20 Transacciones por Segundo (TPS)**
- ✅ Asegurar un **tiempo promedio de respuesta ≤ 1.5 segundos**
- ✅ Mantener una **tasa de error del 0%**

---

## Configuración de la Prueba

### Herramientas utilizadas

- Apache JMeter 5.6.3
- Java JDK 11+
- Postman (validación previa de usuarios)
- CSV con usuarios válidos (`usuarios.csv`)

### Datos utilizados

Archivo CSV con credenciales válidas:

```csv
username,password
mor_2314,83r5^_
donero,ewedon
kevinryan,kev02937@
johnd,m38rmF$
derek,jklg*_56
```

### Parámetros del Thread Group

| Parámetro             | Valor    |
|-----------------------|----------|
| Número de hilos       | 20       |
| Bucle por hilo        | 60       |
| Total de peticiones   | 1200     |
| Ramp-up time          | 1 segundo |

---

## Configuración del HTTP Request

- Método: **POST**
- Endpoint: `https://fakestoreapi.com/auth/login`
- Header: `Content-Type: application/json`
- Body (JSON):

```json
{
  "username": "${username}",
  "password": "${password}"
}
```

- **Aserción usada**: código de respuesta **200**

---

## Resultados Obtenidos

| Métrica                  | Resultado     | Umbral exigido      | Cumple? |
|--------------------------|---------------|----------------------|-----------|
| Total de peticiones      | 1200          | -                    | ✅        |
| Tiempo medio respuesta   | 295 ms        | ≤ 1500 ms            | ✅        |
| Tasa de error            | 0.00%         | ≤ 3%                 | ✅        |
| Rendimiento (Throughput) | 63.7 TPS      | ≥ 20 TPS             | ✅        |

---

## Estructura del Proyecto

```
proyecto-jmeter-login/
├── login-test.jmx
├── usuarios.csv
├── README_final_0porciento.md
├── conclusiones_final.md
├── resultados.csv
├── reporteResumen.jtl
```

---

## Consideraciones Finales

Este README describe el diseño y ejecución exitoso de una prueba de carga realista con usuarios válidos. Para una validación más robusta, consulta `conclusiones.md`.
