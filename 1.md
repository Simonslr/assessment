assessment computer vision python (20 min), sujet en dessous.

Points = documentation (docstring par fonction : description, Args, Returns), interface (titre clair avant chaque clic, print de la taille finale), commentaires sur ce que fait le code. Jamais de plantage. Noms de fonctions du sujet. Que PIL, numpy, matplotlib, scipy.signal. Un seul fichier, tests dans if __name__ == "__main__".

Pas de raise ni validation : doit marcher avec size=10, sigma=3 (taille paire). Gaussien = windows.gaussian + np.outer. Pas d'abs sur Sobel. Images là où le sujet dit.

Clics un par un : x, y = plt.ginput(1, timeout=-1)[0], image en gris convert('L'). Point 1 = celui qui finit à gauche dans le résultat (œil gauche, aile gauche), même si image tournée ou à l'envers ; le titre le dit.

Cibles (où les 2 points tombent dans l'image finale) : visage 100x100 → yeux (30,40),(70,40) ; avion 200x100 → bouts d'ailes (10,50),(190,50) ; sinon selon le sujet. Si absentes : 2 points faciles à cliquer et les plus écartés, choix expliqué en commentaire. Zoom sur les yeux : écart entre yeux = 60% de la largeur de sortie.

Recalage :
1. angle = np.degrees(np.arctan2(y2 - y1, x2 - x1))
2. img.rotate(angle, expand=False)
3. points tournés autour de (w/2, h/2) avec R = [[cos, sin], [-sin, cos]] (y descend)
4. s = distance points tournés / distance cibles
5. crop depuis le point 1 tourné : gauche = x1 - cible_x1*s, haut = y1 - cible_y*s, droite = gauche + largeur*s, bas = haut + hauteur*s, en int
6. resize((largeur, hauteur))

Main : print taille finale, affiche le résultat avec croix rouges sur les cibles.

Fais le .py complet, mais d'abord dis-moi les noms de fonctions et la taille de sortie du sujet.