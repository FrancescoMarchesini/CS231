# MatplotLib

[doc](https://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.plot)

Libreria grafica per stampare a video funzioni etc.. semplice visualizzatore

```python
  import numpy as np
  import matplotlib.pyplot as plt

  # computo le coordinate x e y per i ponti sulla curva sinousidolae
  x = np.arange(0, 3 * np.pi, 0.1)
  y = np.sin(x)

  # plot the points using matplotlib
  plt.plot(x, y)
  plt.show()
```

Esempio di come stampare piu linea nello stesso paragrafo

```python
  import numpy as np
  import matplotlib.pyplot as plt

  # computo le coordinate x e y per i ponti sulla curva sinousidolae
  x = np.arange(0, 3 * np.pi, 0.1)
  y_sin = np.sin(x)
  y_cos = np.cos(x)

  # Plot the points using matplot
  plt.plot(x, y_sin)
  plt.plot(x, y_cos)
  plt.xlabel('x axis label')
  plt.ylabel('y axis label')
  plt.title('Sine and Cosine')
  plt.legend(['Sine', 'Cosine'])
  plt.show()
```

Doppio Plot

```python
  import numpy as np
  import matplotlib.pyplot as plt

  # computo le coordinate x e y per i ponti sulla curva sinousidolae
  x = np.arange(0, 3 * np.pi, 0.1)
  y_sin = np.sin(x)
  y_cos = np.cos(x)

  # Plot di una griglia di immagine di altezza 2 e larghezza 1
  plt.subplot(2, 1, 1)

  # Costruisco il primo plot
  plt.plot(x, y_sin)
  plt.title('Sine')

  # Costruisco il secondo plot come attivo
  plt.subplot(2, 1, 2)
  plt.plot(x, y_cos)
  plt.title('Cosine')

  # Mostra immagine
  plt.show()
```

**Immagini**

```python
  import numpy as np
  from scipy.misc import imread, imresize
  import matplotlib.pyplot as plt

  img = imread('assets/cat.png')
  img_tinted = img * [1, 0.95, 0.9, 1]

  # mostro l'immagine
  plt.subplot(1, 2, 1)
  plt.imshow(img)

  # mostro la nuova immagine
  plt.subplot(1, 2, 2)

  # Esplicito la il cast conversion a uint8 per non genrare possibili
  # problemi
  plt.imshow(np.uint8(img_tinted))
  plt.show()
```
