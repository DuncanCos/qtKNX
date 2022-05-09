# Documentation:

---

- ## comment faire un boutton:

.h

```cpp
QPushButton *monBoutton;
```

.cpp

```cpp
monBoutton = new QPushButton("ceci est un bouton",this);
```

resultat

![](Image/test.png)

- ## comment faire un texte label
- h

```cpp
QLabel *monTexte;
```

.cpp

```cpp
monTexte = new QLabel("ceci est mon texte",this);
```

resultat

![](C:\Users\foxlo\AppData\Roaming\marktext\images\2022-04-12-09-27-28-image.png)

## format des fichier de code:

.h

```cpp
#ifndef MAFEN_H
#define MAFEN_H

#include <QObject>
#include <QWidget>
#include <QLabel>
#include <QPushButton>

class mafen :public QWidget
{
    Q_OBJECT
public:
    mafen();

private:
    QLabel *monTexte;
    QPushButton *monBouton;
};

#endif // MAFEN_H
```

mafen.cpp

```cpp
#include "mafen.h"

mafen::mafen()
{
monTexte = new QLabel("ceci est mon texte",this);
//monBouton = new QPushButton("ceci est un bouton",this);
}
```

main.cpp

```cpp
#include "mafen.h"

#include <QApplication>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
    mafen w;
    w.show();
    return a.exec();
}
```

- ## systeme de layout

Le seul probleme est que les widgets sont superposé entre eux mais on veut pouvoir les placé et cest la qu'intervient les layout

on peut voir les layouts comme un echiquier ou on peut placer les widgets comme on veut.

.h

```cpp
#include <QGridLayout>  
```

.cpp

```cpp
QGridLayout *layout = new QGridLayout;

layout->addWidget(monTexte,0,0);
layout->addWidget(monBouton,1,0);
this->setLayout(layout);
```

 resultat

![](C:\Users\foxlo\AppData\Roaming\marktext\images\2022-04-12-10-00-18-image.png)

voici a quoi ressemble le tableau de layout avec les coordonées

| monTexte 00      | 01     | 02     | 03     |
| ---------------- | ------ | ------ | ------ |
| monBouton **10** | **11** | **12** | **13** |
| **20**           | **21** | **22** | **23** |
| **30**           | **31** | **32** | **33** |

il ya des fonctionnalité en plus par exemple dans cet situation

![](C:\Users\foxlo\AppData\Roaming\marktext\images\2022-04-12-10-28-17-image.png)

et je veux que mon boutton fasse toute la taille de la fenetre il faut alors que je modifie le code tel que:

```cpp
layout->addWidget(monBouton,1,0,1,2);
```

Ce qui nous donne le resultat suivant 

![](C:\Users\foxlo\AppData\Roaming\marktext\images\2022-04-12-10-34-51-image.png)

dans le tableau ça pourrais resembler a ça.

| 00 monTexte | 01 autreTexte | 02  | 03  |
| ----------- | ------------- | --- | --- |
| 10 boutton  | 11boutton     | 12  | 13  |
| 20          | 21            | 22  | 23  |
| 30          | 31            | 32  | 33  |

cela elargie le bouton dans le layout tout simplement.

- ## Les Images

pour faire une image on a besoin d'un QLabel

.h

```cpp
#include <QPixmap>

QLabel *monImage;
```

.cpp

```cpp
imgLabel -> setPixmap(QPixmap("chemin vers l'image/image.png"));
```

mais on peut se dire sa fait long pour le chemin vers limage on peut pas y allez depuis les fichier du projet ? et bien oui on peut.

pour cela allez dans le projet et faire:

Deja dans les fichiers de mon projet je vais ajouter un fichier image pour entreposer tout mes fichier dans un dossier.

Il faut ajouter un QT ressource files

puis on ajoute un fichier existant 

et a la fin on peut changer le code de ce genre : 

```cpp
imgLabel -> setPixmap(QPixmap(":/image/image.png"));
```

## connect des boutton avec le systeme QObject

il existe avec qt un systeme de Qobject et des connect avec des signals et des slots 

par exemple un boutton a un signal clicked le signal est liée  a un slot un slot est une fonction appeler par un slot 

pour tout liee il faut utiliser les connect de qobject 

il ne faut pas oublier d'utiliser les disconnect. 

## se a quoi ressemble le projet avec tout sa

## ajout du systeme de fausse donnée

avec le systemeconnect on peut fait faire un systeme de timer me permettant de generer de fausse donnée

## avec les image

## 

## scaled l'interface pour l'interface en plein ecran

jai du ajouter ces lignes de code pour faire en sorte que les boutton et les images soit scaled avec la fenetre 

## stylesheet

pour ajouter du style a mon interface jai utiliser le stylsheet

## creation final de l'interface

## QComboBox

## creation de l'interface pour les port com

## lien entre les fenetres

## integration avec la partie 1
