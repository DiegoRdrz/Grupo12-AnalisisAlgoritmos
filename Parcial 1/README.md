## Parcial 1
## Punto 4
Solución fuerza bruta:
<img width="1854" height="842" alt="image" src="https://github.com/user-attachments/assets/8c8327b7-230b-4583-b468-dab9513d0496" />

    Código:
    class Solution:
        def maxProfit(self, prices: List[int]) -> int:
            n = len(prices)
            maximun_profit = 0
            for i in range(n):
                for j in range(i + 1, n):
                    if prices[j] > prices[i]:
                        profit = prices[j] - prices[i]
                        
                        if profit > maximun_profit:
                            maximun_profit = profit 
                    
            return maximun_profit

Solución optimizada:
<img width="1854" height="861" alt="image" src="https://github.com/user-attachments/assets/549a0f64-147f-4fe8-9ff9-c99c1236743d" />

Código:
    
    class Solution:
    
        def maxProfit(self, prices: List[int]) -> int:
           
            min_price = prices[0]
           
            max_profit = 0
    
            for i in range(1, len(prices)):
                profit = prices[i] - min_price
                
                if profit > max_profit:
                    max_profit = profit
                
                if prices[i] < min_price:
                    min_price = prices[i]
    
            return max_profit
