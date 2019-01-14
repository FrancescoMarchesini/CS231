# The Magic World of Python

Un semplice esempio di algoritmo di Ordinamento Fatto con Python, giusto per iniziare

```python
      def quicksort(arr):
          #se la lunghezza e minore di 1
          if len(arr) <= 1:
              #ritorno l'array poiche non ce ninete da ordinare
              return arr
          #prendo il punto centrale dell array
          pivot = arr[len(arr) // 2]
          #prendo gli elementi a sinitra del pivot
          left = [x for x in arr if x < pivot]
          #prendo il punto centrale dell'array
          middle = [x for x in arr if x == pivot]
          #prendo gli elementi a destra dell'array
          right = [x for x in arr if x > pivot]

          #ricorsivamente eseguo la funzione fino agli elemnti atomici
          return quicksort(left) + middle + quicksort(right)

      print(quicksort([2, 5, 6, 90, 1, 2, 3]))
```

## Containers

**List**

Sono come array dinamici e possono contenere qualsiasi tipo di Dato

```python
  xs = [3, 1, 2]     #creazione di una lista
  print(xs, xs[2]) 
  print(xs[-1])      #con indice negativo fa il print dall'ultimo valore
  xs.append('bella') #aggiungo un elemento alla lista
  xs.pop()           #tolgo un elemento dalla lista
```

**Slicing**

Metodo per accedere agli elementi di una lista

```python
  nums = list(range(5))
  print(nums)
  print(nums[2:4])
  print(nums[2:]) #stampami tutti gli elementi dal secondo indice in poi
  print(nums[:2]) #stampami tutti gli elementi fino al secondo indice
  print(nums[:])
  nums[2:4] = [8, 9] #assegna ad un particolare range nuovi elementi
```

**Loops**

loop sugli elementi di una lista

```python
  animals = ['cane', 'gatto', 'porco'];
  for animal in animals : 
      print(animal)

  #utilizzo degli indici per accedere agli elementi
  for idx, animal in enumerate(animals):
      print('#%d: %s' % (idx + 1, animal))
```

Modificare gli elementi delle liste

```python
  #Metodologia con la quale trasformare/modificare dati nelle liste
  nums = [0, 1, 2, 3, 4]
  squares = []
  for x in nums:
      squares.append(x ** 2)
  print(squares)

  #tutta quaesta cosa sopra puo essere sintetizzata in
  squares = [x ** 2 for x in nums]
  print(squares)
```

Condizioni all'interno delle liste compresse

```python
  nums = [0, 1, 2, 3, 4]
  #condizionali all'interno delle liste comprsse
  even_square = [x ** 2 for x in nums if x % 2 == 0 ]
  print(even_square)
```

## Dizionari

I dizionario sono array di oggetti che oltre ad evere un value possiedono una key per il value

```python
  #un dizionario e l'insieme di (key, value)
  d = {'chiave' : 'valore', 'chiave2' : 'valore2'};
  print(d['chiave2'])
  d['chiave'] = 'top'; #setto il valore di una chiave
  print(d)
  print(d.get('chiave2', 'N/A'))
  del d['chiave2'] #Togli un elemento dal dizionario
```

**loops**

```python
  d = {'chiave' : 'valore', 'chiave2' : 'valore2'};
  for chiave in d :
      valore = d[chiave]
      print('%s : %s ' % (chiave, valore))
```
**compressioni dizionari**

```python
  #anche i dizionari possono essere compressi con le liste
  lettere = ['a', 'b','c','d','e','f','g','h']
  arr = ['a', 'b', 'c']
  a = [y for y in arr]
  print('%s' % a)
  dizionario = {x : x + 'hhhh' for x in lettere if x != 'a' }
  print(dizionario)
```

## Sets

set sono collezione di elementi non ordinati

```python
  animals = {'cat', 'dog'}

  #add element
  animals.add('fish')

  #revomve
  animals.remove('cat')

  #lunghezza
  print(len(animals))
```

Comprimo la liste

```python
  from math import sqrt
  nums = {int(sqrt(x)) for x in range(30)}
  print(nums)
```

## Tuple

la tupla è una lista di valori immutabile. Una tupla può essere usata come chiave nei dizionari e come elemento del set. mentre le liste no

```python
  d = {(x, x + 1) : x for x in range(10)}
  t = (5, 6)
  print(type(t))
  print(d[t])
  print(d[(1, 2)])
```

## Funzioni
```python
   def sign(x):
    if x > 0:
      return 'positive'
    elif x < 0:
      return 'negative'
    else:
      return 'zero'

    for x in [-1, 0, 1]:
      print(sign(x))
```

 funzioni con argomento
```python
  def hello(name, loud=False):
    if loud:
      print('HELLO, %s!' % name.upper())
    else:
      print('Hello, %s' % name)

  hello('Bob')
  hello('Fred', loud=True)
```
## Classes

Definizione della classe

```python
   
   class Greeter(object):

    # Costruttore 
    def __init__(self, name):
      self.name = name # Creo un istanza di variabile

    # Istanzio un metodo
    def greet(self, loud=False):
      if loud:
        print('Hello, %s!' % self.name.upper())
      else:
        print('Hello, %s' % self.name)
```

Invocazione della classe e dei metodi

```python
  g = Greeter('Fred') # Costruisco un istanza della classe
  g.greet()           # Chiamo un istanza del metodo
  g.greet(loud=True)  # Chimamo uninstanza del metodo
```
