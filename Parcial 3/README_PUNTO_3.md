## 1. SOLUCION
<img width="1858" height="874" alt="image" src="https://github.com/user-attachments/assets/b665a02e-075e-4f65-813a-a77b6efc2864" />

class Solution:
    def numDecodings(self, s: str) -> int:
        n = len(s)
        
        if n == 0 or s[0] == '0':
            return 0
        
        dp = [0] * (n + 1)
        dp[0] = 1
        dp[1] = 1
        
        for i in range(2, n + 1):
            # Tomar un solo dígito
            if s[i - 1] != '0':
                dp[i] += dp[i - 1]
            
            # Tomar dos dígitos
            two_digit = int(s[i - 2:i])
            if 10 <= two_digit <= 26:
                dp[i] += dp[i - 2]
        
        return dp[n]

2. Estrategia de Programación Dinámica

Se construye un arreglo dp de tamaño (n+1) donde dp[i] representa el número de formas de decodificar los primeros i caracteres de la cadena s.

Recurrencia utilizada:

Si el dígito actual s[i-1] es distinto de '0', entonces:

dp[i] += dp[i-1]

Si los dos últimos dígitos forman un número válido entre 10 y 26:

dp[i] += dp[i-2]

La respuesta final se encuentra en dp[n].

3. Justificación

Los casos base:

dp[0] = 1: Hay una forma de decodificar una cadena vacía.
dp[1] = 1: Siempre que el primer carácter no sea '0'.

La recurrencia es correcta porque:

Si el dígito actual no es '0', puede interpretarse como una letra individual, por lo que se suman las formas de decodificar hasta el carácter anterior.
Si los dos últimos dígitos forman un número entre 10 y 26, pueden interpretarse como una sola letra, por lo que se suman las formas de decodificar hasta dos posiciones atrás.
Si aparece un '0', no puede decodificarse solo, por lo que depende únicamente de combinaciones válidas con el dígito anterior (como 10 o 20).

Dado que cada subproblema dp[i] se calcula una sola vez y en orden, se garantiza encontrar la solución óptima global.

4. Complejidad
Complejidad temporal

Se recorre la cadena una sola vez y cada posición se calcula en tiempo constante.

O(n)

donde n es la longitud de la cadena.

Complejidad espacial

Se utiliza un arreglo de tamaño n+1.

O(n)
