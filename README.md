# miau
# Schemat Hornera

Implementacja algorytmu Hornera w języku Python.

## 1. Czym jest schemat Hornera?

Schemat Hornera jest to wspolna nazwa dla dwóch algorytmów
-Algorytmu dzielenia wielomianu przez dwumian liniowy
-Algorytmu obliczania wartości dowolnego wielomianu o jednej zmiennej
### Postać wielomianu

Wielomian w postaci ogólnej:

$`
P(x) = a_n x^n + a_{n-1} x^{n-1} + \dots + a_1 x + a_0
`$

W schemacie Hornera przekształcany jest do postaci:

$P(x) = (\dots((a_n x + a_{n-1})x + a_{n-2})x + \dots + a_1)x + a_0$

Algorytm obliczania 
$`
w(x) &= x(4x^2 - 5x + 7) - 20 =\\
&= x(x(4x-5)+7) - 20,\\

w(2) &= 2(2(4\cdot 2-5)+7)-20 =\\
&= 2(2(8-5)+7) -20 =\\
&= 2(2\cdot 3+7) -20 =\\
&= 2(6+7) -20 =\\
&= 2\cdot 13-20 =\\
&= 26-20 = 6.\\
`$
## 2. Zastosowanie schematu Hornera

Schemat Hornera znajduje zastosowanie w:
- Szybkim obliczaniu wartości wielomianu dla zadanej wartości \( x \),
- Dzieleniu wielomianów przez dwumian \( x - c \),
- Algorytmach numerycznych, takich jak metoda Newtona.

## 3. Implementacja algorytmu w Pythonie

### Obliczanie wartości wielomianu

```python
def horner(coefficients, x):
    """
    Funkcja oblicza wartość wielomianu dla zadanej wartości x
    przy użyciu schematu Hornera.

    :param coefficients: lista współczynników wielomianu [a_n, a_{n-1}, ..., a_0]
    :param x: wartość, dla której liczymy wielomian
    :return: wartość wielomianu
    """
    result = 0
    for coefficient in coefficients:
        result = result * x + coefficient
    return result
```
### Dzielenie wielomianu:

```python
def horner_division(coefficients, c):
    n = len(coefficients)
    quotient = [0] * (n - 1)
    remainder = coefficients[0]
    for i in range(1, n):
        quotient[i - 1] = remainder
        remainder = remainder * c + coefficients[i]
    return quotient, remainder
```
### Dzielenie przez wielomian:
```python
coefficients = [4, -3, 1, 2, -5]
c = 2
quotient, remainder = horner_division(coefficients, c)
print("Quotient:", quotient)  # Wynik: [4, 5, 11, 24]
print("Remainder:", remainder)  # Wynik: 43

