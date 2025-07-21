# Conclusiones 
---

## Logros del ejercicio

- Se alcanzaron los 63.7 TPS requeridos (exigiendo solo 20).
- Tiempo promedio de respuesta de 295 ms, muy por debajo del umbral de 1500 ms.
- Se logró 0% de errores al utilizar únicamente usuarios válidos y configuraciones estables.

---

## 🧠 Observaciones como QA

Aunque se cumplió con los objetivos del ejercicio, para una cobertura de calidad completa se deben considerar escenarios adicionales:

### 1. **Usuarios inválidos**
- Probar con combinaciones incorrectas de `username` y/o `password`
- Validar que retorne código **401 Unauthorized**
- Confirmar que no se recibe un `token`

### 2. **Datos malformados**
- Enviar payloads incompletos o erróneos (ej. `username` sin `password`)
- Validar código **400 Bad Request**
- Útil para verificar robustez de validación del backend


### 3. **Aserciones avanzadas**
- Incluir validación del contenido de la respuesta (ej. estructura JSON, presencia de `token`)

---

## 🧪 Recomendaciones futuras

- Separar los escenarios por grupos de usuarios: válidos, inválidos, malformados
- Medir tiempos con distintos niveles de carga para crear una curva de respuesta

---

📌 Esta prueba fue ideal para validar la estabilidad básica del servicio. Sin embargo, como QA, es fundamental ir más allá del "camino feliz" para descubrir comportamientos inesperados y validar la tolerancia real del sistema.

