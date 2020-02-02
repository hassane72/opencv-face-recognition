***Projet de système de reconnaissance des visages, qui marche en deux phase:
	nous allons d'abord effectuer la détection des visages, extraire les incorporations de visages
	de chaque visage à l'aide d'un apprentissage approfondi(deep learning), former un modèle de reconnaissance des 
	visages sur les incorporations, puis enfin reconnaître les visages dans les images et les flux vidéo avec OpenCV.

***Mode d'utilisation:
	Apres avoir installer les librairie neccessaire a l'utilisation de notre projet a savoir: opencv-python, numpy, Scikit-learn, Pickle, imutils
	Placer vous dans le dossier /code puis taper les commande suivantes:
		la commande suivante pour calculer les incorporations de visage avec OpenCV:
			$ python extract_embeddings.py --dataset dataset --embeddings output/embeddings.pickle --detector face_detection_model --embedding-model openface_nn4.small2.v1.t7
		Apres nous utilison le fichier train_model pour le deep learning qui sera appliquer à nos incorporations de faces extraites:
			$ python train_model.py --embeddings output/embeddings.pickle --recognizer output/recognizer.pickle --le output/le.pickle
		On lance le fichier recognize.py pour la detechtion de visage dans les images:
			$ python recognize.py --detector face_detection_model --embedding-model openface_nn4.small2.v1.t7 --recognizer output/recognizer.pickle 
		Ou si on veut la detection par video on lance la commande suivante:
			$ python recognize_video.py --detector face_detection_model --embedding-model openface_nn4.small2.v1.t7 --recognizer output/recognizer.pickle 