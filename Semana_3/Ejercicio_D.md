# Ejercicio D 
## Comparación de rendimiento

En este ejercicio se comparó el tiempo de ejecución de la versión escalar con la versión que utiliza AVX2, ya que se quería ver la diferencia de rendimiento entre una implementación no vectorizada y una vectorizada.

Para hacer la comparación se utilizaron matrices de tamaño `2048x2048` y una repetición.

### Versión escalar

Primero se ejecutó la versión escalar con:

```bash
make run-scalar
```

Se obtuvieron los siguientes resultados:

```text
Tamano matriz: 2048x2048
Repeticiones: 1
Checksum: 86972906452.000000
C[0][0]: 26800.500000
C[1023][1023]: 26836.500000
Operaciones: 17179869184
Tiempo: 34.893586 segundos
Rendimiento: 0.492350 GFLOP/s
```

### Versión AVX2

Luego se ejecutó la versión vectorizada con:

```bash
make run-avx2
```

Y se obtuvieron estos resultados:

```text
Tamano matriz: 2048x2048
Repeticiones: 1
Checksum: 86972906452.000000
C[0][0]: 26800.500000
C[1023][1023]: 26836.500000
Operaciones: 17179869184
Tiempo: 8.994535 segundos
Rendimiento: 1.910034 GFLOP/s
```

## Comparación de resultados

Se puede ver que las dos versiones obtuvieron el mismo `Checksum` y los mismos valores mostrados de la matriz, por lo que el resultado de la operación se mantuvo igual.

La diferencia se nota principalmente en el tiempo. La versión escalar tardó aproximadamente `34.89 s`, mientras que la versión con AVX2 tardó aproximadamente `8.99 s`.

Para comparar qué tanto mejoró el tiempo, se calculó el speedup de la siguiente manera:

```text
Speedup = Tiempo escalar / Tiempo AVX2

Speedup = 34.893586 / 8.994535

Speedup ≈ 3.88
```

Esto quiere decir que, para esta ejecución, la versión con AVX2 fue aproximadamente **3.88 veces más rápida** que la versión escalar.

También se puede ver la diferencia en el rendimiento, ya que la versión escalar obtuvo `0.492350 GFLOP/s` y la versión AVX2 obtuvo `1.910034 GFLOP/s`. Esto significa que con la versión vectorizada se realizan más operaciones de punto flotante por segundo.

