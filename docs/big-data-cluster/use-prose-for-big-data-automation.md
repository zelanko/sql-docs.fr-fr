---
title: Générer du code pour les tâches de retraitement des données
titleSuffix: Azure Data Studio
description: Cet article décrit comment utiliser l’accélérateur de Code PROSE dans Azure Data Studio pour générer automatiquement le code pour les tâches courantes de retraitement des données.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: f5406ce0e67322a8f7148fc83b83d0789f27e1ae
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66770782"
---
# <a name="data-wrangling-using-prose-code-accelerator"></a>Wrangling de données à l’aide de la PROSE Code accélérateur

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

PROSE Code accélérateur génère le code Python lisible pour vos tâches de retraitement des données. Vous pouvez combiner le code généré avec votre code écrit manuellement de manière transparente tout en travaillant dans un bloc-notes dans Azure Data Studio. Cet article fournit une vue d’ensemble de la façon dont vous pouvez utiliser l’accélérateur de Code.

 > [!NOTE]
 > Programme Synthesis using Examples, également appelé PROSE, est une technologie Microsoft qui génère du code explicite à l’aide d’intelligence artificielle. Il le fait en analyse d’un utilisateur intention ainsi que sur données, générant plusieurs programmes de candidat et choisir le meilleur programme à l’aide d’algorithmes de classement. Pour en savoir plus sur la technologie PROSE, visitez le [page d’accueil de la PROSE](https://microsoft.github.io/prose/).

L’accélérateur de Code est préinstallé avec Azure Data Studio. Vous pouvez l’importer comme tout autre package de Python dans le bloc-notes. Par convention, nous l’importer en tant que cx pour faire plus court.

```python
import prose.codeaccelerator as cx
```

Dans la version actuelle, l’accélérateur de Code peut générer de manière intelligente code Python pour les tâches suivantes :

- Lecture des fichiers de données à un Pandas ou trame de données Pyspark.
- Résolution des types de données dans une trame de données.
- Recherche d’expressions régulières représentant des modèles dans une liste de chaînes.

Pour obtenir une vue d’ensemble des méthodes de l’accélérateur de Code, consultez le [documentation](https://aka.ms/prose-codeaccelerator-overview).

## <a name="reading-data-from-a-file-to-a-dataframe"></a>Lecture des données à partir d’un fichier à une trame de données

Lecture des fichiers à une trame de données implique souvent consulter le contenu du fichier et de déterminer les paramètres corrects à passer à une bibliothèque de chargement de données. Selon la complexité du fichier, l’identification des paramètres corrects peut nécessiter plusieurs itérations.

Accélérateur de Code PROSE résout ce problème en analysant la structure du fichier de données et en générant automatiquement du code pour charger le fichier. Dans la plupart des cas, le code généré analyse les données correctement. Dans certains cas, vous devrez peut-être modifier le code pour répondre à vos besoins.

Prenons l'exemple suivant :

 ```python
import prose.codeaccelerator as cx

# Call the ReadCsvBuilder builder to analyze the file content and generate code to load it
builder = cx.ReadCsvBuilder(r'C:/911.txt')

#Set target to pyspark if generating code to use pyspark library
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
 ```

Le bloc de code précédent imprime le code python suivant pour lire un fichier délimité. Notez comment PROSE détermine automatiquement le nombre de lignes à ignorer, en-têtes, quotechars, séparateurs, etc.

 ```python
import pandas as pd

def read_file(file):
    names = ["lat",
             "lng",
             "desc",
             "zip",
             "title"]

    df = pd.read_csv(file,
        skiprows = 11,
        header = None,
        names = names,
        quotechar = "\"",
        delimiter = "|",
        index_col = False,
        dtype = str,
        na_values = [],
        keep_default_na = False,
        skipinitialspace = True)
    return df
 ```

Accélérateur de code peut générer du code à charge délimités, JSON et les fichiers de largeur fixe à une trame de données. Pour la lecture des fichiers à largeur fixe, le `ReadFwfBuilder` prend éventuellement un fichier de schéma explicite qu’il peut analyser pour obtenir les positions de la colonne. Pour plus d’informations, consultez le [documentation](https://aka.ms/prose-codeaccelerator-docs).

## <a name="fixing-data-types-in-a-dataframe"></a>Résolution des types de données dans une trame de données

Il est courant d’avoir un pandas ou pyspark trame de données avec les types de données est incorrect. Souvent, cela se produit en raison de la non conformes quelques valeurs dans une colonne. Par conséquent, entiers sont lus comme Float ou des chaînes et Dates sont lues en tant que chaînes. L’effort requis pour corriger manuellement les types de données est proportionnelle au nombre de colonnes.

Vous pouvez utiliser le `DetectTypesBuilder` dans ces situations. Cet outil analyse les données, et plutôt que de résoudre les types de données de manière boîte noire, il génère du code pour résoudre les types de données. Le code sert de point de départ. Vous pouvez examiner, utiliser ou modifiez-le si nécessaire.

```python
import prose.codeaccelerator as cx

builder = cx.DetectTypesBuilder(df)

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
```

Pour plus d’informations, consultez le [documentation](https://aka.ms/prose-codeaccelerator-fixtypes).

## <a name="identifying-patterns-in-strings"></a>Identification des modèles dans des chaînes

Un autre scénario courant consiste à détecter les modèles dans une colonne de chaîne à des fins de nettoyage ou de regroupement. Par exemple, peut avoir une colonne de date avec des dates dans plusieurs formats différents. Afin de normaliser les valeurs, vous souhaiterez peut-être écrire des instructions conditionnelles à l’aide d’expressions régulières.


|   |Nom                      |BirthDate      |
|---|:-------------------------|:--------------|
| 0 |Bertram du Plessis        |1995           |
| 1 |Naiara Moravcikova        |Unknown        |
| 2 |Jihoo Spel                |2014           |
| 3 |Viachaslau Gordan Hilario |22-avril-67      |
| 4 |Maya de Villiers          |19-Mar-60      |

Selon le volume et la diversité des données, l’écriture d’expressions régulières pour différents modèles dans la colonne peut être une tâche beaucoup de temps. Le `FindPatternsBuilder` est un outil d’accélération de code puissant qui permet de résoudre le problème ci-dessus en générant des expressions régulières pour obtenir la liste de chaînes.

```python
import prose.codeaccelerator as cx

builder = cx.FindPatternsBuilder(df['BirthDate'])

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

builder.learn().regexes
```

Voici les expressions régulières générées par le `FindPatternsBuilder` pour les données ci-dessus.

```
^[0-9]{2}-[A-Z][a-z]+-[0-9]{2}$
^[0-9]{2}[\s][A-Z][a-z]+[\s][0-9]{4}$
^[0-9]{4}$
^Unknown$
```

En dehors de la génération d’Expressions régulières, `FindPatternsBuilder` peut également générer du code pour les valeurs Regex généré en fonction de clustering. Il peut également déclarer que toutes les valeurs dans une colonne sont conformes aux expressions régulières générées. Pour en savoir plus et découvrir les autres scénarios utiles, consultez le [documentation](https://aka.ms/prose-codeaccelerator-findpatterns).
