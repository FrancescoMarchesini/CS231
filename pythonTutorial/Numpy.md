# Il Magico Mondo di Numpy

[Doc](https://docs.scipy.org/doc/numpy/reference/)

## Array
un numpy array è una griglia di valori, tutti dello stesso tipo, e come indice hanno una tupla di interi non negativi.

il numero di dimensioni è il **rank** dell'array, la **shape** dell'array è una tupla di interi che dice la lunghezza dell'array per ogni dimensione

```python
  import numpy as np

  a = np.array([1, 2, 3]) # Creo un Rank di una Dimensione
  print(type(a))
  print(a.shape)
  print(a[0], a[1], a[2])
  a[0] = 5                # muto l'elemento 0 dell'array
  print(a)

  b = np.array([1, 2, 3], [4, 5, 6]) #Creo un array con 2 Rank
  print(b.shape)
  print(b[0, 0], b[0, 1], b[1,0]) 
```

Utilizzzo di funzioni native Numpy per l generazione di Array

```python
  import numpy as np

  a = np.zeros((2, 2))  #Creo un Array di 2 rank tutti a 0
  b = np.ones(1, 2)     #Creo un Array di tutti 1
  c = np.full((2,2), 7) #Creo un Array costante
  d = np.eye(2)         #Creo a 2x2 identify matrix
  e = np.random.random((2,2))

  print(a, b, c, d, e)
```

## Array Slicing

Come per le liste, si può applicare lo slice su ogni dimensione dell'arrya

```python
  import numpy as np

  #Creo un rank 2 array con shape (3, 4)
  a = np.array([[1, 2, 3, 4], [5, 6, 7, 9], [1, 3, 4, 5]])
  print(a)

  #utilizzo lo slicing per generare un nuovo array che consiste delle prime 2 righe e colonna 1 e 2
  b = a[:2, 1:3]

  #lo slicing e una vista sui dati stessi quindi modificandoli tramite lo slide si modificano
  print(a[0, 1]) 
```

altro sullo slicing per accedere ai dati

```python
  import numpy as np
    
  b = np.array([[1, 2, 3, 4], [5, 6, 7, 9], [1, 3, 4, 5]])

  row_r1 = a[1, :] #accedo alla prima riga dell'array e prendo la colonna
  row_r2 = a[1:2, :] #accedo alle righe 2 e prendo tutti i valori
  print(row_r1, row_r1.shape)
  print(row_r2, row_r2.shape)

  col_r1 = a[: , 1]   #prendo la colonna 1 della matrice
  col_r2 = a[: ; 1:2] #prendo la colonna 2 della matrice
  print(col_r1, col_r1.shape)
  print(col_r2, col_r2.shape)
```
**Integer Array Indexing** : A differenza dello slicing che genera un sotto array dall'array di partenza, *l'integer array index* permette di creare un nuovo array usando i dati di un altro array

```python
  import numpy as np

  a = np.array([[1, 2], [3, 4], [5, 6])

  # Prendo il bulk 1 2 3 e da ogni bulk(row), i primi elementi dell'array
  print(a[1, 2, 3], [0, 0, 0])

  #oppure prendo solo la riga 1 e 2 e gli elementi centrali
  print(a[1, 2], [1, 1])
```

**Trick con gli Indici** : selezionare e mutare elementi di un array tramite un array di indici

```python
  import numpy as np

  #creo un array numpy
  a = np. array([[1, 2, 3], [2, 3, 4], [7, 8, 9, 90], [9, 2, 0, 1, 2]])

  print(a)

  # creao un array di indici che andranno a prendere un elemento specifico del0array a
  b = np.array([0, 2, 3, 4])

  #seleziono un gli elementi di a tramite b
  print(a[np.range(4), b]) #stampa [1, 4, 90, 2]

  #allo stesso tempo posso mutura gli elementi
  a[np.range(4), b] += 10

  print(a)
```

**Boleani ed array** ovvero selezionare degli elementi di un array in base a deteminate condizioni
```python
  import numpy as np
  
  a = np.array([[1, 2], [3,4], [5, 6]])

  #selezionami gli elementi dell'array maggiori di bool_idx
  bool_idx = (a > 2)

  #stampo gli elementi desiderati
  print(a[bool_idx])

  #tutto in manienra concisa
  print(a[a > 2])
```


[Documentazione](https://docs.scipy.org/doc/numpy/reference/arrays.dtypes.html)

Ogni numpy array è un griglia di elementi dello stesso type. Vi è quindi la possibilità di definere con un argomento aggiuntivo che type l'array sia

```python
  import numpy as np

  x = np.array([1, 2])  # Tipo di default
  print(x.dtype)        # Tipo di Default int64

  x = np.array[1.0, 5.2] # Nupy determina da se il tipo
  print(x.dtype)         # Print float64

  x = np.array([1, 2], dytpe=np.int64)  #Forzare numpy ad un particolare tipo
  print(x.dytpe)
```

## Array Math

operazioni matematiche sui vettori

```python
  import numpy as np

  x = np.array([[1, 2], [3, 4]], dtype=np.float64)
  y = np.array([[4, 5], [2, 4]], dtype=np.float64)

  #somma di array
  print(np.add(x, y))  #stessa dicitura x+y

  #sottrazione
  print(np.subtract(x, y))

  #moltiplicazione
  print(np.multiply(x, y))

  #divisione
  print(np.divide(x, y))

  #elevamente a potenza
  print(np.sqrt(x))
```

**prodotto Scalare**

```python
  import numpy as np
  
  x = np.array([[1, 2], [3, 4]])
  y = np.array([[5, 6], [4, 5]])

  v = np.array([9, 10])
  w = np.array([10, 12])

  #prodotto interno dei vettori
  print(np.dot(v, w))

  #prodotto tra vettori / matrici
  print(np.dot(x, v))

  #prodotto tra matrici / matrici
  print(np.dot(x, y))
```

**Sommatori**

```python
  import numpy as no
 
  x = np.array([[1, 2], [3, 4]])

  print(np.sum(x))    #fa la sommatoria di tutti gli elementi degli array
  print(np.sum(x, axis=0))    #sommatoria per ogni colonna
  print(np.sum(x, axis=1))    #sommatoria per ogni riga
```

[Altre funzioni interssanti](https://docs.scipy.org/doc/numpy/reference/routines.math.html)

## BroadCasting

Meccanismo per il quale è possibile fare operazioni aritimentiche su array con diverse forme e dimensioni. Es Utilizzare un array piu piccolo e fare operazioni su un array piu grande

```python
  #vogliamo aggiungere un vettore costante ad ogni riga di una matrice..  ovveero aggiunger V ad ogni Riga di X
  x = np.array([[1, 2, 3], [3, 6, 90], [90, 1, 3]])
  y = np.array([100, 0, 100])
  y = np.empty_like(x) #creo una matrixe della stessa shape e dim di x

  #aggiungo
  for i in range(4):
    y[i, : ] = x[i, : ]+v

  print(y)
```

Questo metodo non è cosi efficente poichè fa la seguente cosa: ovvero generare per ogni row della matrice un array y e fare l'operazione aritmetica deserata..

```python
  #implementazione 
  x = np.array([[1, 2, 3], [3, 6, 90], [90, 1, 3]])
  y = np.array([100, 0, 100])
  yy = np.tile(y, (3, 1)) #impilo uno sopra l'latro 3 copie di y
  print(yy)

  z = x + yy;
  print(z)
```

Con il meccanismo di **brodcasting** possiamo bypassare la copia e quindi ottimizzare il todos

```python
  import numpy as np

  x = x = np.array([[1,2,3], [4,5,6], [7,8,9], [10, 11, 12]])
  v = np.array([1, 0, 1])

  y = x + v
  print(y)
```

**Funionzi Universali** ovvero funzioni che implementano i meccensismo del bradcsatstig

```python
  import numpy as np
  
  #computa il prodotto scalere
  v = np.array([1, 2, 3])
  w = np.array(4, 4)

  #Trasformo la matrcie v in un vettore e faccio prodotto scalare 
  print(np.reshape(v, (3, 1) * w)

  #Aggiungi vettore alla matrice
  x = np.array([[1, 2, 3], [4, 5, 6]])
  print(x + v)

  #aggiungi un vettore ad ogni colonna della matrice
  print((x.T + w).T)

  # ....
```
