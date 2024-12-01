
# Algorytm Euklidesa  

## 1. Co to jest?  
Algorytm Euklidesa to jeden z najstarszych znanych algorytmów matematycznych, który służy do wyznaczania największego wspólnego dzielnika (NWD) dwóch liczb naturalnych \( a \) i \( b \). Jest prosty i bardzo wydajny, a jego zastosowanie można spotkać w wielu dziedzinach, takich jak teoria liczb, kryptografia czy informatyka.

---

## 2. Dwie wersje Algorytmu Euklidesa

### a) Niezoptymalizowany Algorytm Euklidesa (odejmowanie):  
- **Zasada działania:** Algorytm działa poprzez iteracyjne odejmowanie mniejszej liczby od większej, aż obie liczby staną się równe. Wynik tej liczby to NWD.  
- **Zalety:** Łatwy do zrozumienia i zaimplementowania.  
- **Wady:** Wydajność spada dla dużych liczb, ponieważ liczba operacji zależy od wartości większej liczby.  

### b) Optymalny Algorytm Euklidesa (modulo):  
- **Zasada działania:** Algorytm wykorzystuje operację modulo (\( a \mod b \)) zamiast odejmowania. Mniejsza liczba zostaje zastąpiona resztą z dzielenia \( a \) przez \( b \), co pozwala szybciej osiągnąć wynik.  
- **Zalety:** Dużo szybszy dzięki logarytmicznej złożoności czasowej.  
- **Wady:** Wymaga zrozumienia operacji modulo, co może być mniej intuicyjne dla początkujących.  

---

## 3. Działanie algorytmu na przykładach  

### Przykład: Wyznacz NWD(48, 18):  

#### Niezoptymalizowany algorytm (odejmowanie):  
1. \( a = 48, b = 18 \): \( a > b \), więc \( a = a - b = 48 - 18 = 30 \).  
2. \( a = 30, b = 18 \): \( a > b \), więc \( a = a - b = 30 - 18 = 12 \).  
3. \( a = 12, b = 18 \): \( b > a \), więc \( b = b - a = 18 - 12 = 6 \).  
4. \( a = 12, b = 6 \): \( a > b \), więc \( a = a - b = 12 - 6 = 6 \).  
5. \( a = 6, b = 6 \): \( a = b = 6 \).
6. Wynik: \( NWD(48, 18) = 6 \).  

#### Optymalny algorytm (modulo):  
1. \( a = 48, b = 18 \): \( a \mod b = 48 \mod 18 = 12 \), więc \( a = 18, b = 12 \).  
2. \( a = 18, b = 12 \): \( a \mod b = 18 \mod 12 = 6 \), więc \( a = 12, b = 6 \).  
3. \( a = 12, b = 6 \): \( a \mod b = 12 \mod 6 = 0 \), więc \( NWD = b = 6 \).  

Oba algorytmy dają ten sam wynik \( NWD(48, 18) = 6 \), ale wersja optymalna wymaga mniej operacji.  

---

## 4. Implementacja w Pythonie  

### Optymalny algorytm rekurencyjny:  
```python
def nwd_rek(a, b):
    if b == 0:
        return a
    return nwd_rek(b, a % b)
```

### Optymalny algorytm interacyjny:  
```python
def nwd_iter(a, b):
    while b != 0:
        a, b = b, a % b
    return a
```

---

## 5. Złożoność obliczeniowa  

| Algorytm                    | Złożoność czasowa               
|-----------------------------|---------------------------------|
| **Niezoptymalizowany**      | \( O(max(a, b)) \)            |         
| **Optymalny (modulo)**      | \( O(log(min(a, b))) \)      
---

## 6. Zadania do rozwiązania  

1. Oblicz NWD za pomocą obu wersji algorytmu dla liczb:  
   - \( (a, b) = (144, 84) \)  
   - \( (a, b) = (255, 75) \)  
   - \( (a, b) = (1001, 847) \)  
   - \( (a, b) = (3600, 1260) \)  

2. Porównaj czas działania obu wersji dla dużych liczb, np. \( (a, b) = (123456, 987654) \).  

---

## 7. Podsumowanie  
Algorytm Euklidesa w obu wersjach jest niezwykle prosty i skuteczny. Niezoptymalizowana wersja (odejmowanie) jest dobrym punktem startowym dla początkujących, ale w praktyce zdecydowanie zaleca się stosowanie wersji optymalnej (modulo) ze względu na jej wydajność.
