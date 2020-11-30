# Design pattern

Par définition un **Design pattern** ou **Patron de conception** en français est est une solution générique d'implémentation répondant à un problème spécifique. Il s'agit d'une solution à un problème dans un contexte spécifique.

## Il existe 3 grands types de design pattern

- le **patron de création** (**creational patterns**) 
- le **patron de structure**  (**structural patterns** )
- le **patron de comportement** (**behavioral patterns**) 

## Patron de création
Un patron de création permet de résoudre les problèmes liés à la création et la configuration d'objets. Ils fonctionnent indépendamment de la façon dont les objets individuels sont créés et représentés dans un logiciel.
- **Singleton**:  utilisé quand une classe ne peut être instanciée qu'une seule fois.
- **Prototype**:  permet de créer un nouvel objet par recopie d'un objet existant. La création de ce nouvel objet se fait sans passer par l'appel du constructeur et la configuration de la valeur de ses attributs
- **Fabrique**: Ce patron permet la création d'un objet dont la classe dépend des paramètres de construction (un nom de classe par exemple).
- **Fabrique abstraite**: Ce patron permet de gérer différentes fabriques concrètes à travers l'interface d'une fabrique abstraite.
- **Moteur**: Ce patron permet la construction d'objets complexes en construisant chacune de ses parties sans dépendre de la représentation concrète de celles-ci.

## Patron de structure
Un patron de structure permet de résoudre les problèmes liés à la structuration des classes et leur interface en particulier.
**Pont**:  Utilisation d'interface à la place d'implémentation spécifique pour permettre l'indépendance entre l'utilisation et l'implémentation.
- **Façade**:    permet de simplifier l'utilisation d'une interface complexe.
- **Adaptateur**:  Ce patron permet d'adapter une interface existante à une autre interface.
- **Objet composite**: Ce patron permet de manipuler des objets composites à travers la même interface que les éléments dont ils sont constitués.
- **Proxy**: Ce patron permet de substituer une classe à une autre en utilisant la même interface afin de contrôler l'accès à la classe (contrôle de sécurité ou appel de méthodes à distance).
- **Poids-mouche**: Ce patron permet de diminuer le nombre de classes créées en regroupant les classes similaires en une seule et en passant les paramètres supplémentaires aux méthodes appelées.
- **Décorateur**: Ce patron permet d'attacher dynamiquement de nouvelles responsabilités à un objet. Ils offrent une alternative assez souple à l'héritage pour composer de nouvelles fonctionnalités.

## Patron de comportement
Un patron de comportement permet de résoudre les problèmes liés aux comportements, à l'interaction entre les classes.
- **Chaîne de responsabilité**:  Permet de construire une chaîne de traitement d'une même requête.
- **Commande**:  Encapsule l'invocation d'une commande.
- **Interpréteur**: Interpréter un langage spécialisé.
- **Observateur**: Intercepter un événement pour le traiter.
- **Itérateur**: Parcourir un ensemble d'objets à l'aide d'un objet de contexte (curseur).
- **Stratégie**: Changer dynamiquement de stratégie (algorithme) selon le contexte.
- **Visiteur**: Découpler classes et traitements, afin de pouvoir ajouter de nouveaux traitements sans ajouter de nouvelles méthodes aux classes existantes.
- **Médiateur**: Réduire les dépendances entre un groupe de classes en utilisant une classe Médiateur comme intermédiaire de communication.
- **Mémento**: Mémoriser l'état d'un objet pour pouvoir le restaurer ensuite.
- **Patron de méthode**: Définir un modèle de méthode en utilisant des méthodes abstraites.
- **Etat**: Gérer différents états à l'aide de différentes classes.

# Avantages

- Amélioration de la documentation de conception
- Facilitation de la réutilisation réussie de conception
- Amélioration de la compréhensibilité des conceptions
- Réduction de temps de développement
- Facilitation de communication entre les développeurs grâce à l'utilisation d'un langage commun  
