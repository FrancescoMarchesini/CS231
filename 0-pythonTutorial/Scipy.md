# Scipy

Wrapper di numpy con varie funzioni matematiche per lavorare su vettori e matrici molto molto comonde.

```python
    from scipy.misc import imread, imsave, imresize

    # read PNG Image in  numpy Array
    img = imread('assets/cat.png')
    print(img.dtype, img.shape)

    # tramite il meccenismo di broadcasting posso fare il resise dell'immagine in modo efficente

    # RGB lascio inalterato il canale R mentre modifico iL G e B A
    img_tinted = img * [1, 0.95, 0.9, 1]

    # Infiene faccio il resize dell'immagine  a 300*300
    img_tinted = imresize(img_tinted, (300, 300))

    # Scrivo su disco la nuova immagine
    imsave('assets/cat_tineded.png', img_tinted)
```

Calcolo della distanza tra punti
[doc](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.distance.pdist.html
)
```python
  import numpy as np
  from scipy.spatial.distance import pdist, squareform

  #creo un array dove ogni row è un punto nello spaziono 2d
  x = np.array([[0, 1], [1, 0], [2, 0]])
  print(x)

  #Computo della distanza euclidea tra due punti
  d = squareform(pdist(x, 'euclidean'))
  print(d)
```
