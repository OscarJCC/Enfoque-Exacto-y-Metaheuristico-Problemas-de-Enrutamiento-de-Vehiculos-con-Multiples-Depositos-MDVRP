# Enfoque Exacto y Metaheurístico en Problemas de Enrutamiento de Vehículos con Múltiples Depósitos (MDVRP)

Descripción general

Este proyecto aborda el Problema de Ruteo de Vehículos con Múltiples Depósitos (MDVRP) mediante dos enfoques:

Modelo exacto (MILP)

Enfoque matheurístico (cluster-first, route-second)

El objetivo es minimizar la distancia total recorrida por una flota de vehículos con capacidad limitada que deben atender a un conjunto de clientes desde múltiples depósitos.

Metodología

1. Modelo Exacto (MILP)

Se formula el problema como un modelo de programación lineal entera mixta, donde:

Variables binarias representan rutas entre nodos

Variables continuas controlan la carga del vehículo

Se incluyen restricciones de:

visita única por cliente

conservación de flujo

capacidad del vehículo

eliminación de subciclos (MTZ)

Este enfoque garantiza optimalidad global, pero es computacionalmente costoso.

2. Enfoque Matheurístico

Se implementa una estrategia de descomposición en dos etapas:

a) Clustering (heurística constructiva)

Los clientes se ordenan por demanda

Se asignan al depósito más cercano respetando capacidad

b) Resolución por subproblemas (CVRP)

Cada cluster se resuelve como un problema independiente

Se utiliza MILP para cada subproblema

✔ Ventaja: reducción significativa del tiempo computacional❌ Desventaja: no garantiza optimalidad global

⚙️ Tecnologías utilizadas

Julia

JuMP (modelado matemático)

HiGHS (solver MILP)

Plots.jl (visualización)
