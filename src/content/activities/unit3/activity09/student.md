1.  .

+ en c++

  + original se imprime como (70, 80)

   + copia se modifica a (100, 200)

  +  original sigue siendo (70, 80)

+ en c#
  + Modifica copia a (100, 200)

  + Al imprimir original, también aparece como (100, 200)
    
2.  en c++ copia es un objeto diferente con las mismas propiedades de original, mientras que en c# es otro puntero que apunta al mismo objeto en el heap
