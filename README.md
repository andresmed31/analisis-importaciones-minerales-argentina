# Importaciones minerales de Argentina (1994–2025)

Análisis exploratorio de más de 100.000 registros mensuales de importaciones minerales argentinas: qué se importa, de dónde viene, cómo evolucionó el valor en tres décadas y qué explica el salto de 2021.

**Herramientas:** Python · pandas · NumPy · Matplotlib · Jupyter Notebook

---

## Resumen de hallazgos

| Pregunta | Resultado |
|---|---|
| ¿Qué minerales concentran el valor importado? | **Hierro 40,0 %** y **aluminio 17,8 %** del CIF acumulado: juntos, 57,9 % |
| ¿De dónde viene? | **Brasil 58,8 %** del valor acumulado; Australia (7,3 %) y Chile (7,0 %) le siguen de lejos |
| ¿Cuándo se importó más? | Máximo en **2011**: USD 2.297,5 millones nominales |
| ¿Cuándo creció y cayó más? | Mayor suba: **2021 (+116,5 %)**. Mayor caída: **2009 (−59,3 %)** |
| ¿Qué explica 2021? | El **hierro** aporta USD 711,5 millones del aumento, y **Brasil** USD 632,5 millones de ese incremento |
| Caso uranio | En 2025 se importaron USD 62,8 millones; el 39,9 % con país de origen distinto al de procedencia |

> Todos los valores son **CIF nominales en USD**. No permiten separar precios de cantidades ni demostrar causas económicas.

---

## Contenido del notebook

1. **Carga y diagnóstico:** dimensiones, tipos, nulos y duplicados.
2. **Preparación y corte temporal:** fecha mensual, años completos (1994–2025), 2026 parcial excluido.
3. **Composición histórica:** ranking de minerales y de países de origen, con participación acumulada.
4. **Evolución anual:** nivel y variación interanual del CIF.
5. **Descomposición de 2021:** aporte de cada mineral al salto (gráfico de cascada con verificación contable) y desglose del hierro por país.
6. **Participación de los minerales:** ocho principales + "Otros".
7. **Evolución por mineral:** trayectorias de los ocho principales.
8. **Caso de estudio, uranio:** coincidencia entre país de origen y de procedencia, ponderada por valor.

## Decisiones metodológicas

- **Años completos:** las comparaciones anuales llegan hasta 2025; 2026 (datos hasta junio) queda afuera.
- **Faltantes:** los 4 registros sin país se agrupan como "Sin dato". Un año sin filas no se interpreta como importaciones nulas.
- **Porcentajes sobre base comparable:** en el caso del uranio, el denominador son solo los registros con ambos países informados.
- **Control de consistencia:** la cascada de 2021 incluye un `assert` que verifica que los aportes suman exactamente la diferencia entre ambos años.
- **Dato a contrastar:** en 2024 el uranio tiene una sola fila por USD 55,55; se señala como posible inconsistencia y no se interpreta.

## Limitaciones

- Valores nominales: no están ajustados por inflación, lo que distorsiona comparaciones entre décadas.
- Los rankings históricos suman todo el período y no representan necesariamente la estructura actual.
- Cada fila es un registro de la base, no necesariamente una operación individual.
- Diferencias entre origen y procedencia no prueban por sí solas intermediación ni rutas físicas.
- Pendiente: completar las definiciones oficiales de los campos de la fuente (por ejemplo, `PPRO`).

## Cómo reproducirlo

```bash
pip install pandas numpy matplotlib jupyter
jupyter notebook analisis_minerales_argentina.ipynb
```

Colocá el CSV en la misma carpeta que el notebook, con el nombre que espera la celda de carga (`impominerales-siacam(3).csv`).

## Datos

- **Fuente:** SIACAM (según el nombre del archivo). `<COMPLETAR: enlace de descarga>`
- **Fecha de consulta:** `<COMPLETAR>`
- **Cobertura:** enero de 1994 a junio de 2026; 101 grupos minerales, 152 países de origen, 5 sectores.

## Próximos pasos

- [ ] Deflactar los valores (USD constantes) para comparar décadas.
- [ ] Plantear y contrastar una hipótesis sobre el salto de 2021 con precios internacionales del mineral de hierro.
- [ ] Medir la concentración por origen a lo largo del tiempo.
- [ ] Analizar estacionalidad con la columna `MES` y el desglose por `SECTOR`.
- [ ] Replicar las consultas clave en SQL.
- [ ] Armar un dashboard interactivo.

## Autor

`<COMPLETAR: nombre>` · `<COMPLETAR: enlace a perfil / LinkedIn / Workana>`
