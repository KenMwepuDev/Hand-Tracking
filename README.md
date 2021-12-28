# Faire un système de tracking des mains (Hands Tracking) avec python et mediapipe
 Le tracking d’une main avec **mediapipe**  se fait en traquent des points localisé sur une main come sur la forme ci-dessous:
 ![image](https://user-images.githubusercontent.com/61374882/147406775-82134980-3b1b-47dd-b09b-e99fa3ffbf20.png)
![image](https://user-images.githubusercontent.com/61374882/147406846-11abe0fc-7f74-4ea6-9a5d-20431658ef1a.png)
![image](https://user-images.githubusercontent.com/61374882/147406847-b25bb670-e8be-4739-8a10-0373425c3c02.png)

Premièrement vous devez installer la librairie mediapipe grâce à la commande suivante sous :
-	Windows: pip install mediapipe
-	Linux: 
-	Mac Os:

![image](https://user-images.githubusercontent.com/61374882/147406885-ef144241-0d32-463c-88b5-06d46d7261f0.png)
*mediapipe est une librairie développé par Google pour faire du Computer Vision avec python*

Et après on installe la libraire **Open cv** qui nous permettra dans notre contexte de pouvoir démarrer une vidéo stocké sur l’ordinateur (ou un support externe) ou/et de démarrer la webcam de la machine (ou externe), ainsi que de pouvoir mettre des éléments sur la vidéo. La commande pour l’installer sous :
-	Windows: **pip install opencv**
-	Linux: 
-	Mac Os:

Et maintenant pour débuter avec le code on commence par importer open cv et mediapipe


`import cv2`    
`import mediapipe as mp`

Ensuite on récupère la vidéo soit de la machine comme suite :

`>cap = cv2.VideoCapture(r'chemin_du_fichier')`

Ou de la webcam comme suite :

`>cap = cv2.VideoCapture(0)`

![image](https://user-images.githubusercontent.com/61374882/147406885-ef144241-0d32-463c-88b5-06d46d7261f0.png)
*Le nombre entre parenthèse représente le code de la webcam (0 est pour la première webcam détecté)*

On à la vidéo maintenant on va créer l’objet **hands** qui nous permettra de détecter les mains (droites et gauche) sur la vidéo ainsi que de récupérer les différents coordonnées de ce derniers.

On crée aussi l’objet **drawing_utils** que nous utiliserons pour pouvoir tracer de ligne représentant la forme de la main sur celles détectés sur chaque frame de la vidéo.

`>mpDraw = mp.solutions.drawing_utils`

![image](https://user-images.githubusercontent.com/61374882/147406885-ef144241-0d32-463c-88b5-06d46d7261f0.png)
*Une Frame est l’image composant la vidéo, car une vidéo n’est que la succession de plusieurs Frames qui passe l’une après l’autre*

*! On peut comparer une Frame à une Image.*

Et après cela on crée l’objet **Hands**
`>Hands = mpHands.Hands()`

Et pour finir on écrit le code qui tournera dans une boucle jusqu’à ce que l’utilisateur puisse appuyer sur la touche **« D »** du clavier.

>`while (True):`
>
>`    success, img = cap.read() #On lit une image (frame) de la vidéo`
>
>`    imgRGB = cv2.cvtColor(img, cv2.COLOR_BGR2RGB) #On convertie l’image qui est en BGR en RGB`
>
>`    result = Hands.process(imgRGB) #Détecte la mains et récupère ces coordonnés`
>
>`    if (result.multi_hand_landmarks): #Vérifie si le résultat ne pas nulle`
>
>`       #Traçage des lignes`
>
>` for handLms in result.multi_hand_landmarks:`
>
>`            for id,lm in enumerate(handLms.landmark):`
>
>`                h, w, c = img.shape`
>
>`                cx, cy = int(lm.x*w), int(lm.y*h)`
>
>`                if (id == 0):`
>
>`                    cv2.circle(img, (cx, cy), 25, (255, 0, 255), cv2.FILLED)`
>
>`           mpDraw.draw_landmarks(img, handLms, mpHands.HAND_CONNECTIONS)`
>
>`    CurrentTime = time.time()
>
>`    fps = 1/(CurrentTime - PreviousTime)`     
>    
>`    PreviousTime = CurrentTime`
>
>`    cv2.putText(img, str(int(fps)), (10, 70), cv2.FONT_HERSHEY_PLAIN, 3, (255, 0, 255), 2)`
>
>`    cv2.imshow("Frame", img)`
>    
>`    if cv2.waitKey(20) & 0xFF==ord('d')`
>
>`        break`
>
>`cap.release()`    
> 
>`cv2.destroyAllWindows()`
