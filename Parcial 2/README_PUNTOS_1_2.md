## Ejercicios 1 y 2 
## Punto 1

Solución:
![alt text](imgs/image-1.png)

```cpp
codigo:
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        sort(g.begin(), g.end());
        sort(s.begin(), s.end());

        int i = 0; // niños
        int j = 0; // galletas
        int content = 0;

        while (i < g.size() && j < s.size()) {
            if (s[j] >= g[i]) {
                content++;
                i++;
                j++;
            } else {
                j++;
            }
        }

        return content;
    }
};
```

## Justificación Greedy

Ordenar permite satisfacer primero a los niños **menos exigentes** con las galletas **más pequeñas posibles**.  
Esto deja las galletas grandes disponibles para niños con mayor *greed*, maximizando el número total de niños satisfechos.

---

## Complejidad

### Tiempo

- Ordenar niños: `O(n log n)`
- Ordenar galletas: `O(m log m)`
- Recorrido con dos punteros: `O(n + m)`

**Complejidad total:**
O(n log n + m log m)

### Espacio
O(1)

*(sin contar el espacio utilizado por el algoritmo de ordenamiento).*


## Punto 2

Solución:
![alt text](imgs/image-2.png)
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> seen;

        for (int num : nums) {
            if (seen.find(num) != seen.end()) {
                return true;
            }
            seen.insert(num);
        }

        return false; 
    }
};

## Justificación Greedy

Ordenar por **menor tiempo de finalización (`end`)** permite escoger siempre el intervalo que deja **más espacio disponible** para los siguientes.

Cuando aparece un solapamiento, eliminar el intervalo que **termina más tarde** garantiza que el conjunto restante tenga mayor posibilidad de acomodar más intervalos sin generar conflictos.

Este enfoque sigue el mismo principio del problema clásico **Activity Selection**, donde elegir la actividad que termina primero maximiza el número de actividades compatibles.

---

## Complejidad

### Tiempo

- Ordenar intervalos: `O(n log n)`
- Recorrido del arreglo: `O(n)`

**Complejidad total:**
O(n log n)

### Espacio
O(1)
