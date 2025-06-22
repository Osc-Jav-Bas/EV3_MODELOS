# EV3_MODELOS
# Presentación: Factores asociados al uso de métodos de barrera en la última relación sexual

## 1. Portada
**Título:** Factores asociados al uso de métodos de barrera en la última relación sexual  
**Integrantes:** Oscar Silva y Bastián González  
**Sección:** BIY 7122-002D  
**Fecha:** 18 de junio de 2025  
**Logo:** Duoc UC

---

## 2. Introducción
La ENSSEX es una encuesta nacional del Ministerio de Salud de Chile que recopila información sobre comportamientos sexuales, acceso a educación y uso de métodos preventivos.

**Objetivo:** Identificar los factores que influyen en el uso de métodos de barrera (como el preservativo) en la última relación sexual.

**Muestra:** 20.392 personas, 923 variables  
**Herramientas:** R (dplyr, ggplot2, caret, pROC), modelos: logístico, árbol de decisión, random forest

---

## 3. Pregunta de investigación
> ¿Qué factores están asociados al uso de preservativo en la última relación sexual?

**Variable dependiente:** `p120_o1` → `uso_preservativo` (0 = no, 1 = sí)

---

## 4. Variables independientes seleccionadas (15)
| Código | Descripción | Tipo | Transformación |
|--------|-------------|------|----------------|
| `p5` | Nivel educacional | Ordinal | Alta (1) / Baja (0) |
| `p1` | Sexo | Categórica | Factor |
| `p7` | Estado civil | Categórica | En relación (1) / Soltero (0) |
| `p38` | Educación sexual escolar | Ordinal | Buena (1) / Mala (0) |
| `p34` | Educación sexual familiar | Ordinal | Recibida (1) / No (0) |
| `i_3_p26` | Consumo de alcohol en relaciones | Binaria | Sí (1) / No (0) |
| `i_7_p25` | Uso de poppers | Binaria | Sí (1) / No (0) |
| `i_1_p33` | Placer femenino con condón | Ordinal | Afecta (1) / No afecta (0) |
| `i_2_p33` | Placer masculino con condón | Ordinal | Afecta (1) / No afecta (0) |
| `i_1_p102` | Uso de juguetes sexuales | Binaria | Sí (1) / No (0) |
| `i_7_p28` | Sexo solo con amor | Ordinal | Sí (1) / No (0) |
| `i_6_p102` | Infidelidad | Binaria | Sí (1) / No (0) |
| `p109` | Buscar sexo por apps | Binaria | Sí (1) / No (0) |
| `edad` | Edad | Numérica | Mantiene valor |
| `p103_o1` | Alcohol reciente en sexo | Binaria | Sí (1) / No (0) |

---

## 5. Limpieza y modelado
- Transformación de variables a binario o factor.
- Manejo de datos faltantes con filtrado o imputación.
- Creación de `data2` como base limpia para modelado.

```r
uso_preservativo <- if_else(p120_o1 %in% 1:13, 1L, 0L)
```

---

## 6. Gráficos descriptivos

### Uso de preservativo por sexo
![sexo](./uso%20preservativo%20por%20sexo.png)
> Las mujeres reportan mayor uso que los hombres.

### Situación amorosa y uso
![pareja](./uso%20de%20preservativo%20segun%20situacion%20amorosa.png)
> Menor uso en relaciones estables: confianza reduce percepción de riesgo.

### Educación sexual escolar
![educacion](./uso%20presservativo%20segun%20educacion%20escolar.png)
> Recibir educación sexual formal mejora el uso del preservativo.

---

## 7. Modelos predictivos

### Árbol de decisión
![arbol](./modelode%20arbol.png)
> Variables clave: educación, pareja, uso de apps, juguetes sexuales.

### Random Forest
![rf](./modelo%20bosque.png)
> Las variables más importantes: educación familiar, apps, alcohol, juguetes.

### Curva ROC
![roc](./curvas%20roc.png)
> Punto óptimo: 0.34. AUC ~ 0.75. Buen balance sensibilidad/especificidad.

---

## 8. Conclusiones
- Mayor educación formal y sexual escolar = mayor uso de condón.
- El consumo de alcohol y drogas disminuye uso preventivo.
- En relaciones estables baja la percepción de riesgo.
- Apps y juguetes sexuales reflejan nuevos escenarios sexuales.

---

## 9. Recomendaciones
- Fomentar educación sexual integral sin estigmas.
- Campañas dirigidas a jóvenes, apps, consumidores de alcohol.
- Intervenciones para relaciones estables (bajo riesgo percibido).
- Incluir tecnologías sexuales en estrategias preventivas.

---

## 10. Cierre
Gracias por su atención.  
Presentación basada 100% en el informe EV3 y códigos reales de ENSSEX.

---

### Repositorio: https://osc-jav-bas.github.io/EV3_MDD/
