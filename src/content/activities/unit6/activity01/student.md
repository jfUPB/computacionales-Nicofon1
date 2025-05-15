+ Describe con tus propias palabras el comportamiento general de la aplicación. ¿Qué ves en pantalla?
  + un monton de particulas de 3 tamaños y colores diferentes,por defecto no hay interacciones pero con teclas se puede atraer o repeler las particulas respecto a posicion del cursor

+ ¿Cómo puedes interactuar con la aplicación? Menciona específicamente las teclas y qué efecto parecen tener sobre las partículas.
  + si r las repele del cursor a las atrae del curson y n es como un neutro q todas se detienen por un pequeño lapso y dps se siguen moviendo suavemente y s para todo

+ ¿Observas diferentes tipos de “partículas” (elementos visuales)? ¿Se comportan todas igual inicialmente?
  + hay tres categorias  grande azul verda mediano y rojas pequeñas y no logro notar un comportamiento diferente entre ellas 

+ Toma algunas capturas de pantalla de la aplicación en diferentes momentos (estado inicial, después de presionar ‘a’, ‘r’, ‘s’, ‘n’) y añádelas a tu bitácora.
  + init
![image](https://github.com/user-attachments/assets/c3337856-bdfa-4b95-ab97-f39cb7d61b99)

  + a
![image](https://github.com/user-attachments/assets/a698d9a4-7210-4a77-806f-eb8b79dbcb53)

  + r
![image](https://github.com/user-attachments/assets/780e7bcf-b732-47c5-a726-808dec108adc)

  + n
![image](https://github.com/user-attachments/assets/beda5a26-1184-45f8-9eca-541f69b71385)
![image](https://github.com/user-attachments/assets/42d3d060-71f2-4b93-ad05-112758d6f644)

+ ¿Qué crees que está pasando “detrás de cámaras” cuando presionas las teclas? Formula una hipótesis inicial sobre cómo la aplicación cambia el comportamiento de las partículas.
  + en init ps cada particula tiene una direccion y velocidad aleatoria y n hace eso tmbn pero antes de eso detiene todas las ezferas un lapso para quitarles la velocidad
  + r le añade una fuerza de repulcion a la posicion del cursor y a una de atraccion y depende de la optimizacion por cada esfera se han de calcular esas fuerzas
