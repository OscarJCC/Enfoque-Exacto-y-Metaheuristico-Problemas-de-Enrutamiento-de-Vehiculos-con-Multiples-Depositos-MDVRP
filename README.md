# Enfoque Exacto y Metaheurístico en Problemas de Enrutamiento de Vehículos con Múltiples Depósitos (MDVRP)

## Descripción general

Este proyecto aborda el **Problema de Ruteo de Vehículos con Múltiples Depósitos (MDVRP)** mediante dos enfoques:

1. **Modelo exacto (MILP)**
2. **Enfoque matheurístico (cluster-first, route-second)**

El objetivo es **minimizar la distancia total recorrida** por una flota de vehículos con capacidad limitada que deben atender a un conjunto de clientes desde múltiples depósitos.

---

##  Metodología

###  1. Modelo Exacto (MILP)

Se formula el problema como un modelo de **programación lineal entera mixta**, donde:

* Variables binarias representan rutas entre nodos
* Variables continuas controlan la carga del vehículo
* Se incluyen restricciones de:

  * visita única por cliente
  * conservación de flujo
  * capacidad del vehículo
  * eliminación de subciclos (MTZ)

Este enfoque garantiza **optimalidad global**, pero es computacionalmente costoso.

---

###  2. Enfoque Matheurístico

Se implementa una estrategia de descomposición en dos etapas:

#### a) Clustering (heurística constructiva)

* Los clientes se ordenan por demanda
* Se asignan al depósito más cercano respetando capacidad

#### b) Resolución por subproblemas (CVRP)

* Cada cluster se resuelve como un problema independiente
* Se utiliza MILP para cada subproblema

Ventaja: reducción significativa del tiempo computacional
Desventaja: no garantiza optimalidad global

---

## ⚙️ Tecnologías utilizadas

* **Julia**
* **JuMP** (modelado matemático)
* **HiGHS** (solver MILP)
* **Plots.jl** (visualización)

---

## 📂 Estructura del proyecto

```
MDVRP/
│
├── MDVRP-Instances-master/
├── Modelo_Metaheuristico.ipynb
├── Modelo_Exacto.ipynb
├── Enfoque_Exacto_y_Metaheurístico_en_Problemas_de_Ruteo_de_Vehículos_con_Múltiples_Depósitos__MDVRP_.pdf
├── Resultados/
├   ├── Datos_Solucion
│   ├── Graficas_Modelo_Exacto/
│   └── Graficas_Modelo_Metaheuritico/
└── README.md
```

## 📊 Resultados

Se evalúan los siguientes indicadores:

* Costo total
* Tiempo computacional

Los resultados se almacenan en:

* Archivos `.txt` (Datos_Solucion)
* Gráficas `.png`

---

## 📈 Visualización

Se generan:

* Rutas por depósito
* Rutas por vehículo

---

## Consideraciones computacionales

* Límite de tiempo: 200–300 segundos
* Gap relativo: 10%
* Medición de tiempo:

  * `@elapsed` (tiempo total)

---

## 📚 Conclusiones esperadas

* El modelo exacto obtiene soluciones óptimas pero con alto costo computacional
* El enfoque matheurístico reduce tiempos significativamente
* Existe un compromiso entre calidad de solución y tiempo

---

## Autor

Proyecto desarrollado como parte de estudios en optimización y simulación.

---

## Futuro trabajo

* Implementación de metaheurísticas (GA, Tabu Search)
* Paralelización de subproblemas
* Comparación con benchmarks estándar

