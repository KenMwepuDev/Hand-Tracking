# Faire un système de tracking des mains (Hands Tracking) avec python et mediapipe
 Le tracking d’une main avec mediapipe  se fait en traquent des points localisé sur une main come sur la forme ci-dessous:
 ![image](https://user-images.githubusercontent.com/61374882/147406775-82134980-3b1b-47dd-b09b-e99fa3ffbf20.png)
![image](https://user-images.githubusercontent.com/61374882/147406846-11abe0fc-7f74-4ea6-9a5d-20431658ef1a.png)
![image](https://user-images.githubusercontent.com/61374882/147406847-b25bb670-e8be-4739-8a10-0373425c3c02.png)

Premièrement vous devez installer la librairie mediapipe grâce à la commande suivante sous :
-	Windows: pip install mediapipe
-	Linux: 
-	Mac Os:

![image](https://user-images.githubusercontent.com/61374882/147406885-ef144241-0d32-463c-88b5-06d46d7261f0.png)
mediapipe est une librairie développé par Google pour faire du Computer Vision avec python

Et après on installe la libraire open cv qui nous permettra dans notre contexte de pouvoir démarrer une vidéo stocké sur l’ordinateur (ou un support externe) ou/et de démarrer la webcam de la machine (ou externe), ainsi que de pouvoir mettre des éléments sur la vidéo. La commande pour l’installer sous :
-	Windows: pip install opencv
-	Linux: 
-	Mac Os:

Et maintenant pour débuter avec le code on commence par importer open cv et mediapipe

import cv2
import mediapipe as mp
