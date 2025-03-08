# Projet : Modélisation UML Automatisée avec NLP

## Objectif
L'objectif de ce projet est de développer une **intelligence artificielle (IA)** capable de générer des **modèles UML** (Unified Modeling Language) et une **documentation technique** à partir d'un cahier des charges. Ce projet combine des techniques de **traitement du langage naturel (NLP)** et de **génie logiciel** pour automatiser la modélisation UML.

---

## Contexte et Historique
En tant qu'étudiant en **Master Réseaux et Systèmes Informatiques** à la faculté des sciences et techniques de Settat, ma formation se concentre sur le **développement web** et les **techniques de génie logiciel**. L'un des aspects clés de cette formation est la **modélisation UML**, qui permet de représenter visuellement les systèmes logiciels.

Cependant, la création manuelle de diagrammes UML peut être **chronophage** et sujette à des erreurs. Ce projet vise à automatiser ce processus en utilisant des techniques de **NLP** pour analyser un cahier des charges et générer automatiquement des diagrammes UML (comme les diagrammes de cas d'utilisation et de classes) ainsi qu'une documentation associée.

---

## Introduction au NLP
Le **traitement automatique du langage naturel (NLP)** est une branche de l'intelligence artificielle qui permet aux machines de comprendre, d'interpréter et de générer du langage humain. Il combine des techniques de **linguistique**, d'**informatique** et d'**apprentissage automatique** pour traiter des données textuelles.

### Applications du NLP
- **Tokenisation** : Découper un texte en mots ou phrases.
- **Analyse syntaxique** : Comprendre la structure grammaticale d'une phrase.
- **Reconnaissance d'entités nommées** : Identifier des noms propres (personnes, lieux, etc.).
- **Génération de texte** : Produire du texte à partir de données structurées.

---

## Analyse Linguistique et Conception UML
L'analyse linguistique permet de comprendre comment les éléments du langage naturel peuvent être traduits en concepts UML. Par exemple :
- Les **noms** et **groupes nominaux** représentent des **classes** ou **entités**.
- Les **verbes** indiquent des **associations** entre ces classes.
- Les **articles définis/indéfinis** (comme "le", "un") indiquent la **multiplicité** des entités.

### Exemple
- **Phrase** : "L'utilisateur peut créer un projet."
- **Analyse** :
  - **Sujet** : "L'utilisateur" → Classe `Utilisateur`.
  - **Verbe** : "créer" → Association `créer`.
  - **Complément** : "un projet" → Classe `Projet`.

---

## Outils et Technologies
### Langages et Bibliothèques
- **Python** : Langage de programmation principal.
- **SpaCy** : Bibliothèque NLP pour le traitement du langage naturel.
- **RE (Expressions Régulières)** : Pour la recherche de motifs dans le texte.
- **VS Code** : Environnement de développement.

### Fonctionnalités de SpaCy
- **Tokenisation** : Découpage du texte en mots.
- **Étiquetage morphosyntaxique** : Identification des classes grammaticales.
- **Reconnaissance d'entités nommées** : Détection des noms propres.
- **Analyse de dépendances** : Compréhension des relations entre les mots.

---

## Diagramme de Cas d'Utilisation
### Définition
Un **diagramme de cas d'utilisation** décrit les fonctionnalités d'un système du point de vue des utilisateurs. Il identifie les **acteurs** (utilisateurs) et les **cas d'utilisation** (actions).

### Extraction des Cas d'Utilisation
1. **Identifier les verbes** : Les verbes à l'infinitif (comme "créer", "supprimer") indiquent des actions.
2. **Identifier les sujets** : Les sujets doivent être des **êtres humains** ou des **acteurs**.
3. **Extraire les groupes nominaux** : Ils représentent les objets sur lesquels portent les actions.

### Exemple
- **Phrase** : "L'administrateur peut créer un projet."
- **Cas d'utilisation** : "créer un projet".

---

## Procédure de Code
### Étapes
1. **Extraire les phrases** contenant des sujets humains.
2. **Identifier les verbes** à l'infinitif.
3. **Vérifier si le sujet** est un être humain.
4. **Extraire les groupes nominaux** associés aux verbes.
5. **Générer les cas d'utilisation** à partir des verbes et groupes nominaux.

### Exemple de Code
```python
import spacy

# Charger le modèle de langue française
nlp = spacy.load("fr_core_news_sm")

# Texte d'exemple
text = """
L'administrateur peut créer un projet.
L'utilisateur peut supprimer un fichier.
"""

# Analyser le texte
for sentence in nlp(text).sents:
    for token in sentence:
        if token.pos_ == "VERB" and token.lemma_ in ["pouvoir", "devoir"]:
            print(f"Cas d'utilisation : {token.text} {sentence[token.i+1:]}")
```

---

---

## Ressources
- [Documentation de SpaCy](https://spacy.io/api/doc)
- [Guide des expressions régulières en Python](https://docs.python.org/3/library/re.html)
- [Tutoriel UML](https://www.uml.org/)

---
