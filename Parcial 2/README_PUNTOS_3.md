## Punto 3
## Solución:

```cpp
Código:
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int maxReach = 0;

        for (int i = 0; i < nums.size(); i++) {
            if (i > maxReach) {
                return false;
            }

            maxReach = max(maxReach, i + nums[i]);
        }

        return true;
    }
};
```

## Estrategia Greedy

La idea es mantener siempre el máximo índice al que podemos llegar mientras recorremos el arreglo.

En cada posición i, verificamos si podemos alcanzarla.
Si es alcanzable, actualizamos el máximo alcance posible usando el salto permitido en esa posición (i + nums[i]).

Si en algún momento encontramos una posición que no podemos alcanzar, significa que no es posible llegar al final del arreglo.

## Justificación del enfoque Greedy

El algoritmo toma una decisión local en cada paso: actualizar el índice más lejano que se puede alcanzar hasta el momento.

Esto funciona porque:

Si podemos llegar a una posición i, entonces podemos intentar extender nuestro alcance usando el salto disponible en esa posición.

Siempre conservamos el mayor alcance posible, lo cual maximiza nuestras opciones futuras.

Si en algún punto el índice actual supera el alcance máximo (i > maxReach), significa que no existe ninguna forma de llegar a esa posición desde los saltos anteriores.

Por lo tanto, mantener actualizado el mayor índice alcanzable garantiza que si existe un camino al final, el algoritmo lo detectará.

Esta estrategia cumple con la propiedad greedy porque la mejor decisión local (extender el alcance máximo) conduce a la solución global correcta.

## Complejidad
Tiempo

Sea:

n = tamaño del arreglo nums

Entonces:

Recorrido del arreglo:
O(n)

Complejidad total:
O(n)

### Espacio

O(1)

Ya que solo se utiliza una variable adicional (maxReach) y no se requiere memoria extra proporcional al tamaño del arreglo.
