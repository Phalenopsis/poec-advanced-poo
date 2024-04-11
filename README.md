
# Exercice de POO avancé 🤯

L'objectif de ce challenge est de mettre le plus possible en pratique les notions de POO/clean code/design patterns afin de créer une architecture objet la plus évolutive et maintenable possible.

C 'est un exercice **délicat**. 


TIPS : 
👉 Prendre le temps de **concevoir** les objets et leurs interactions avant de commencer à coder. La phase de conception ici est indispensable. 
👉 Encapsuler ce qui **varie** .
👉 Utiliser l'héritage, avec **parcimonie**. 
👉 Utiliser la **composition**.
👉 Utiliser les **interfaces** 
👉 Le **Design Pattern** `template method`  pourrait être utile...


## Contexte 👨‍⚕️

Vous créez une application à but médical. En entrée, vos utilisateurs répondent à un quizz qui permet, en fonction des réponses obtenues, de mettre en relation l'utilisateur (le patient) avec un médecin adapté à son `besoin médical`, sa `localisation` et ses `préférences relationnelles`.

L'application ne sera utilisée qu'en France. 

  

## Les objets à créer

  ### Patient
  Un patient à les caractéristiques suivantes : 
  * `nom et prénom`
  * `Localisation`
  * `Profil relationnel`
  * `Besoin médical`


### Médecin

Votre application propose un ensemble de médecins. Chaque médecin possède un `nom et prénom`, un `coût`, une `spécialisation médicale`, une `localisation`, et un `profil relationnel`.

  
  

### Profil relationnel

Le `profil relationnel` s'établit en  faisant la moyenne des 4 indicateurs : `accueil`, `gentillesse`, `écoute` et `pédagogie`. Chaque indicateur se mesure sur 5. La pondération de chaque indicateur n'est pas la même : 
* `Gentillesse` et `écoute` pèsent 2 fois plus dans le profil relationnel
* `Accueil` ne pèse que 0.5 fois
* `Pédagogie` pèse 1.

  
  

### Localisation

La `localisation` est composée de :
*  `n° de la rue`
* `rue`
* `Ville`
*  `Code postal`
*  `complément`

Son format doit correspondre à celui qu'attend Google Maps API.

  

### Coût

* La base de calcul d'une `consultation` est de 50€. Celle d'une `intervention` est de 300€.

* Si le médecin consulte en cabinet et que sa moyenne relationnelle est supérieure à **3** , il faut multiplier le coût de la consultation par 2,5.

* S'il officie en clinique, il faut multiplier par 6 le prix de la consultation en cabinet.

* Si le médecin est aussi chirurgien, il faut ajouter 145€ à la base de calcul. Si le médecin n'est que chirurgien, il faut en revanche n'ajouter que 90€.

* Si le médecin est neurologue et chirurgien , il faut multiplier par 3 le prix de son intervention.

* La sécurité sociale base ses remboursements sur le prix `hopital`, et non pas `clinique`. Elle rembourse à hauteur de :

* 100% du prix si l'utilisateur à un profil relationnel à 90% compatible

* 80% du prix si l'utilisateur à un profil relationnel à 50% à 90% compatible

* 50% du prix si l'utilisateur à un profil relationnel à 50% et moins

Ce que la sécurité sociale ne rembourse pas en clinique peut être remboursé par la complémentaire du patient, s'il en a une. 

  

### Spécialisation médicale

* Un médecin peut être soit : `généraliste`, `rhumatologue`, `cardiologue`, `neurologue`, `chirurgien` ou `dentiste`.

* Tous possèdent un `cabinet`, sauf le chirurgien.
* Le `chirurgien` ne possède pas de `cabinet`, mais il opère en `clinique` ou en `hôpital`. 

* Le `cabinet`, la  `clinique` ou `l'hôpital`possèdent tous une `localisation`

* Le `neurologue` peut aussi être `chirurgien`.

* Le `dentiste` est systématiquement `chirurgien`.

  

### le Chirurgien

* Peut opérer en `clinique` ou en `hopital`. Son prix est 6 fois supérieur en clinique.
* A une `équipe` à encadrer.
* A  un profil relationnel : 3 - 2 - 3 - 1

  

### Le Généraliste

* Officie en `cabinet` uniquement. 
* Il a un partenariat avec les pharmarcies locales pour vendre de la `moraline` et du `motivex`
* A un profil relationnel : 3 - 3 - 3 - 3


### Le Rhumatologue

* Officie en `cabinet` uniquement. 
* Vend aussi des `prothèses`
* A un profil relationnel : 2 - 3 - 4 - 3


### Le Cardiologue

* Officie en `cabinet` et en `clinique`. 
* Partage son lieu de travail avec une `nutritioniste`
* A un profil relationnel : 4 - 3 - 3 - 4

### Le Neurologue

* Officie en `cabinet`, en `clinique` et en `hopital` (s'il est aussi chirurgien)
* A un profil relationnel : 2 - 4 - 5 - 2
* Peut aussi être chirurgien 

### Le Dentiste

* Officie en `cabinet` et en `clinique`. 
* A un profil relationnel : 1 - 3 - 2 - 1
* Est systématiquement `chirurgien`

### Chaque médecin
* A sa propre façon de consulter, pour ceux qui font des consultations
* A sa propre façon d'opérer, pour ceux qui dont des interventions.
 

  

# Zé barti ! Bonne chance ! 🤩
