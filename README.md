# 🎮 ¿Qué hace exitoso a un videojuego? Análisis de ventas 1980–2016

Análisis exploratorio y estadístico de más de 16.000 videojuegos para identificar qué plataformas, géneros y clasificaciones impulsan las ventas, y en qué apostar para una campaña de marketing en 2017.

**👉 Empieza aquí:** [`video_game_sales_analysis.ipynb`](video_game_sales_analysis.ipynb), con todo el código, los gráficos y las conclusiones.

---

## Contexto y problema

**Ice** es una tienda online que vende videojuegos en todo el mundo y necesita decidir en qué juegos y plataformas invertir su presupuesto publicitario de 2017. Con datos históricos de ventas por región, reseñas de usuarios y de la crítica, géneros, plataformas y clasificación ESRB, el objetivo fue responder:

- ¿Qué plataformas están creciendo y cuáles están desapareciendo?
- ¿Qué géneros son más rentables?
- ¿Influyen las reseñas en las ventas?
- ¿Cambia el perfil del jugador entre Norteamérica, Europa y Japón?

## Mi contribución

Proyecto individual. Me encargué de todo el proceso: limpieza y preparación de los datos, análisis exploratorio, visualizaciones, perfiles por región, pruebas de hipótesis y conclusiones.

## Cómo abordé el trabajo: decisiones clave

- **Valores ausentes sin distorsionar el análisis.** En lugar de imputar con la media o la mediana (la media de `year_of_release` es 2006, e imputarla habría inflado artificialmente ese año), marqué los ausentes y los valores `TBD` con `-1`, un valor fuera de rango que se filtra fácilmente antes de graficar o calcular.
- **Elegir el periodo relevante.** Calculé que una plataforma tarda en promedio **~7,6 años** en desaparecer. Como el objetivo era pronosticar 2017, acoté el modelo a **2013–2016** para no arrastrar tendencias de consolas que ya no existen.
- **Rentabilidad por género con promedios, no totales.** El total de ventas favorece a los géneros con muchos lanzamientos, así que comparé las ventas promedio por juego para medir la rentabilidad real.
- **Comparación justa entre plataformas.** Para comparar el mismo juego en distintas consolas, filtré solo los títulos disponibles en las cuatro principales (PS3, PS4, X360 y Xbox One).
- **Validación estadística.** Usé pruebas t (`scipy.stats`, α = 0,05) para contrastar diferencias en las calificaciones de usuarios.

## Resultados

| Pregunta | Hallazgo |
|---|---|
| Plataformas con más potencial en 2017 | **PS4** y **Xbox One**, las únicas con tendencia de crecimiento antes de 2016 |
| Plataformas líderes del periodo | PS4, Xbox One y PS3 |
| Géneros | Acción, Shooter y Deportes lideran. En promedio venden **~3,7 veces más** que Puzzle, Estrategia y Aventura |
| Reseñas vs. ventas | Correlación positiva pero **baja**. La crítica profesional pesa más que las reseñas de usuarios |
| Perfil por región | NA y UE: PS4 lidera (27,8 % y 40,8 % del mercado), con Acción y Shooter al frente y la clasificación `M` como la más vendida. **Japón es distinto:** lidera Nintendo 3DS (28,6 %), el segundo género es Role-Playing y la clasificación más vendida es `T` |
| Hipótesis 1: calificaciones Xbox One vs. PC | Son **diferentes** (p ≈ 1,4·10⁻⁵) |
| Hipótesis 2: calificaciones Acción vs. Deportes | **Sin diferencia significativa** (p ≈ 0,11) |

**Recomendación:** concentrar la campaña de 2017 en juegos de Acción y Shooter para PS4 y Xbox One en Norteamérica y Europa, con una estrategia diferenciada para Japón (Nintendo 3DS, juegos de rol y clasificación `T`).

**Limitaciones:** los datos de 2016 parecen incompletos, por lo que la caída de ventas de ese año puede estar sobreestimada. Además, muchos juegos antiguos no tienen reseñas ni clasificación.

## Herramientas

Python · pandas · NumPy · matplotlib · seaborn · SciPy · Jupyter Notebook

## Archivos

| Archivo | Descripción |
|---|---|
| `video_game_sales_analysis.ipynb` | Notebook con el análisis completo |
| `games.csv` | Dataset (ventas, reseñas, plataforma, género y clasificación ESRB) |

Para ejecutarlo: `pip install pandas numpy matplotlib seaborn scipy jupyter` y luego abre el notebook en la misma carpeta que `games.csv`.

---

**Sebastián Camilo Guarín Novoa** · [LinkedIn](https://www.linkedin.com/in/sebastian-guarin/) · sguarin96@gmail.com
