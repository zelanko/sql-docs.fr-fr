---
title: Optimisation des performances pour les résultats
description: Cet article est un résumé des méthodes, résultats et conclusions de deux études de cas ayant testé plusieurs méthodes d’optimisation.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 03/29/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a6afdda3975fc8f6c269f9c1fcbca35318f0c4da
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88179992"
---
# <a name="performance-for-r-services-results-and-resources"></a>Performances pour R Services : résultats et ressources
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Cet article est le quatrième et le dernier d’une série qui décrit l’optimisation des performances pour R Services. Cet article est un résumé des méthodes, résultats et conclusions de deux études de cas ayant testé plusieurs méthodes d’optimisation.

Les deux études de cas avaient des objectifs différents :

+ La première, menée par l’équipe de développement R Services, cherchait à mesurer l’impact de techniques d’optimisation spécifiques
+ La seconde, dirigée par une équipe de scientifiques des données, cherchait à tester plusieurs méthodes pour déterminer les meilleures optimisations d’un scénario de scoring de volume élevé spécifique.

Cette rubrique répertorie les résultats détaillés de la première étude de cas. Pour la seconde étude de cas, un résumé décrit les résultats globaux. À la fin de cette rubrique, vous trouverez des liens vers tous les scripts et exemples de données, ainsi que des ressources utilisées par les auteurs d’origine.

## <a name="performance-case-study-airline-dataset"></a>Étude de cas sur les performances : Jeu de données Airline

Cette étude de cas menée par l’équipe de développement SQL Server R Services cherchait à tester les effets de différentes optimisations. Un modèle rxLogit unique a été créé et un scoring réalisé sur le jeu de données Airline. Les optimisations ont été appliquées pendant les processus de formation et de scoring pour évaluer les impacts individuels.

- GitHub : [Exemple de données et de scripts](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning) pour l’étude des optimisations de SQL Server

### <a name="test-methods"></a>Méthodes de test

1. Le jeu de données Airline est constitué d’une seule table de 10 millions de lignes. Il a été téléchargé et chargé en masse dans SQL Server.
2. Six copies de la table ont été effectuées.
3. Diverses modifications ont été appliquées aux copies de la table, afin de tester des fonctionnalités de SQL Server telles que la compression de pages, la compression de lignes, l’indexation, le stockage de données en colonnes, etc.
4. Les performances ont été mesurées avant et après l’application de chaque optimisation.

| Nom de la table| Description|
|------|------|
| *airline* | Données converties à partir du fichier xdf d’origine à l’aide de `rxDataStep`|                          |
| *airlineWithIntCol*   | Chaîne *DayOfWeek* convertie en entier. Colonne *rowNum* également ajoutée.|
| *airlineWithIndex*    | Mêmes données que dans la table *airlineWithIntCol*, mais avec un seul index cluster utilisant la colonne *rowNum*.|
| *airlineWithPageComp* | Mêmes données que dans la table *airlineWithIndex*, mais avec la compression de page activée. Deux colonnes également ajoutées, *CRSDepHour* et *Late*, qui sont calculées à partir de *CRSDepTime* et *ArrDelay*. |
| *airlineWithRowComp*  | Mêmes données que dans la table *airlineWithIndex*, mais avec la compression de ligne activée. Deux colonnes également ajoutées, *CRSDepHour* et *Late*, qui sont calculées à partir de *CRSDepTime* et *ArrDelay*. |
| *airlineColumnar*     | Stockage en colonnes avec un seul index cluster. Table remplie avec les données d’un fichier csv nettoyé.|

Chaque test se composait des étapes suivantes :

1. Une opération garbage collection R a été induite avant chaque test.
2. Un modèle de régression logistique a été créé en fonction des données de la table. La valeur de *rowsPerRead* a été définie sur 500 000 pour chaque test.
3. Les scores ont été générés à l’aide du modèle formé
4. Chaque test a été exécuté six fois. Le temps de la première exécution (« exécution à froid ») n’a pas été conservé. Pour autoriser une valeur aberrante occasionnelle, le temps **maximal** pour les cinq exécutions restantes n’a pas été conservé non plus. Le temps d’exécution écoulé moyen de chaque test a été calculé à partir de la moyenne des quatre exécutions restantes.
5. Les tests ont été exécutés à l’aide du paramètre *reportProgress* avec la valeur 3 (= rapporter les temps et la progression). Chaque fichier de sortie contient des informations sur le temps d’E/S, le temps de transition et le temps de calcul. Ces informations sont utiles pour le diagnostic et la résolution des problèmes.
6. La sortie de la console était également dirigée vers un fichier stocké dans le répertoire de sortie.
7. Les scripts de test ont traité les temps de ces fichiers pour calculer la durée moyenne des exécutions.

Par exemple, les résultats suivants correspondent aux temps d’un test unique. Les valeurs les plus intéressantes sont **Total read time** (le temps d’E/S) et **Transition time** (le temps passé à créer les processus de calcul).

**Exemples de temps**

```text
Running IntCol Test. Using airlineWithIntCol table.
run 1 took 3.66 seconds
run 2 took 3.44 seconds
run 3 took 3.44 seconds
run 4 took 3.44 seconds
run 5 took 3.45 seconds
run 6 took 3.75 seconds
  
Average Time: 3.4425
metric time pct
1 Total time 3.4425 100.00
2 Overall compute time 2.8512 82.82
3 Total read time 2.5378 73.72
4 Transition time 0.5913 17.18
5 Total non IO time 0.3134 9.10
```

Nous vous recommandons de télécharger et de modifier les scripts de test pour vous aider à résoudre les problèmes liés à R Services ou aux fonctions RevoScaleR.

### <a name="test-results-all"></a>Résultats de tests (tous)

Cette section compare les résultats avant et après pour chacun des tests.

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>Taille des données avec compression et un stockage de tables en colonnes

Le premier test comparait l’utilisation de la compression et d’une table en colonnes pour réduire la taille des données.

| Nom de la table            | Lignes     | Réservé   | Données       | index_size | Inutilisé  | % gagné (réservé) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10 000 000 | 2 978 816 Ko | 2 972 160 Ko | 6 128 Ko    | 528 Ko  | 0                   |
| *airlineWithPageComp* | 10 000 000 | 625 784 Ko  | 623 744 Ko  | 1 352 Ko    | 688 Ko  | 79 %                 |
| *airlineWithRowComp*  | 10 000 000 | 1 262 520 KB | 1 258 880 Ko | 2 552 Ko    | 1 088 Ko | 58 %                 |
| *airlineColumnar*     | 9 999 999  | 201 992 Ko  | 201 624 Ko  | n/a        | 368 Ko  | 93 %                 |

**Conclusions**

La réduction de la taille des données a été le plus efficace en appliquant un index columnstore, suivi d’une compression de pages.

#### <a name="effects-of-compression"></a>Effets de la compression

Ce test comparait les avantages de la compression de lignes, la compression de pages et d’aucune compression. Un modèle a été formé à l’aide de `rxLinMod` sur les données issues de trois tables de données différentes. La même formule et requête a été utilisée pour toutes les tables.

| Nom de la table            | Nom du test       | numTasks | Temps moyen |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | 1        | 5,6775       |
|                       | NoCompression - parallel| 4        | 5,1775       |
| *airlineWithPageComp* | PageCompression | 1        | 6,7875       |
|                       | PageCompression - parallel | 4        | 5,3225       |
| *airlineWithRowComp*  | RowCompression  | 1        | 6,1325       |
|                       | RowCompression - parallel  | 4        | 5,2375       |

**Conclusions**

La compression seule ne semble pas être utile. Dans cet exemple, l’augmentation de l’UC pour gérer la compression compense la diminution du temps d’E/S.

Toutefois, quand le test est exécuté en parallèle en définissant *numTasks* sur 4, le temps moyen diminue.

L’effet de la compression peut être plus significatif pour les jeux de données volumineux. La compression varie selon le jeu de données et les valeurs. Vous avez donc intérêt à faire plusieurs tests pour évaluer l’effet de la compression sur votre jeu de données.

### <a name="effect-of-windows-power-plan-options"></a>Effet des options du mode de gestion de l’alimentation de Windows

Dans cette expérience, `rxLinMod` a été utilisé avec la table *airlineWithIntCol*. Le mode de gestion de l’alimentation de Windows a été défini avec l’option **Équilibré** ou **Performances élevées**. Pour tous les tests, *numTasks* a été défini sur 1. Le test a été exécuté six fois, à raison de deux fois avec chaque option de gestion de l’alimentation pour étudier la variabilité des résultats.

Option de gestion de l’alimentation **Performances élevées** :

| Nom du test | Exécutez \# | Temps écoulé | Temps moyen |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,57 secondes |              |
|           | 2      | 3,45 secondes |              |
|           | 3      | 3,45 secondes |              |
|           | 4      | 3,55 secondes |              |
|           | 5      | 3,55 secondes |              |
|           | 6      | 3,45 secondes |              |
|           |        |              | 3,475        |
|           | 1      | 3,45 secondes |              |
|           | 2      | 3,53 secondes |              |
|           | 3      | 3,63 secondes |              |
|           | 4      | 3,49 secondes |              |
|           | 5      | 3,54 secondes |              |
|           | 6      | 3,47 secondes |              |
|           |        |              | 3,5075       |

Option de gestion de l’alimentation **Équilibré** :

| Nom du test | Exécutez \# | Temps écoulé | Temps moyen |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,89 secondes |              |
|           | 2      | 4,15 secondes |              |
|           | 3      | 3,77 secondes |              |
|           | 4      | 5 secondes    |              |
|           | 5      | 3,92 secondes |              |
|           | 6      | 3,8 secondes  |              |
|           |        |              | 3,91         |
|           | 1      | 3,82 secondes |              |
|           | 2      | 3,84 secondes |              |
|           | 3      | 3,86 secondes |              |
|           | 4      | 4,07 secondes |              |
|           | 5      | 4,86 secondes |              |
|           | 6      | 3,75 secondes |              |
|           |        |              | 3,88         |

**Conclusions**

Le temps d’exécution est plus cohérent et rapide quand l’option de mode de gestion de l’alimentation **Performances élevées** de Windows est utilisée.

#### <a name="using-integer-vs-strings-in-formulas"></a>Comparaison entre l’utilisation d’entiers et de chaînes dans les formules

Ce test a évalué l’impact de la modification du code R afin d’éviter un problème courant avec les facteurs de chaîne. Plus précisément, un modèle a été formé à l’aide de `rxLinMod` avec deux tables : dans la première, les facteurs sont stockés sous forme de chaînes et dans la seconde, les facteurs sont stockés sous forme d’entiers.

+ Pour la table *airline*, la colonne [DayOfWeek] contient des chaînes. Le paramètre _colInfo_ a été utilisé pour spécifier les niveaux de facteur (Monday, Tuesday, etc.)

+  Pour la table *airlineWithIndex*, [DayOfWeek] est un entier. Le paramètre _colInfo_ n’a pas été spécifié.

+ Dans les deux cas, la même formule a été utilisée : `ArrDelay ~ CRSDepTime + DayOfWeek`.

| Nom de la table          | Nom du test   | Temps moyen |
|---------------------|-------------|--------------|
| *Airline*           | *FactorCol* | 10,72        |
| *airlineWithIntCol* | *IntCol*    | 3,4475       |

**Conclusions**

L’utilisation de nombres entiers plutôt que de chaînes pour les facteurs présente un avantage évident.

### <a name="avoiding-transformation-functions"></a>Exécution sans les fonctions de transformation

Dans ce test, un modèle a été formé à l’aide de `rxLinMod`, mais le code a été modifié entre les deux exécutions :

+ Lors de la première exécution, une fonction de transformation a été appliquée dans le cadre de la génération du modèle. 
+ Lors de la seconde exécution, les valeurs de caractéristique étaient précalculées et disponibles, afin qu’aucune fonction de transformation ne soit requise.

| Nom du test             | Temps moyen |
|-----------------------|--------------|
| WithTransformation    | 5,1675       |
| WithoutTransformation | 4,7          |

**Conclusions**

Le temps de formation était plus bref **sans** l’utilisation d’une fonction de transformation. En d’autres termes, le modèle a été formé plus rapidement en utilisant des colonnes précalculées et rendues persistantes dans la table.

Le temps gagne devrait être d’autant plus important avec un plus grand nombre de transformations et un jeu de données plus volumineux (\> 100 millions).

### <a name="using-columnar-store"></a>Utilisation du stockage en colonnes

Ce test a évalué les avantages en matière de performances de l’utilisation d’un index et d’un stockage de données en colonnes. Le même modèle a été formé à l’aide de `rxLinMod` et sans transformation de données.

+ Lors de la première exécution, la table de données utilisait un stockage de lignes standard.
+ Lors de la deuxième exécution, un stockage en colonnes a été utilisé.

| Nom de la table         | Nom du test | Temps moyen |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4.67         |
| *airlineColumnar*  | ColStore  | 4,555        |

**Conclusions**

Les performances sont plus élevées avec le stockage en colonnes qu’avec le stockage de lignes standard. Une amélioration significative des performances peut être attendue pour les jeux de données plus volumineux (\> 100 millions).

### <a name="effect-of-using-the-cube-parameter"></a>Effet de l’utilisation du paramètre cube

L’objectif de ce test consistait à déterminer si l’option dans RevoScaleR pour utiliser le paramètre **cube** précalculé pouvait améliorer les performances. Un modèle a été formé à l’aide de `rxLinMod`, avec la formule suivante :

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

Dans la table, les facteurs *DayOfWeek* sont stockés sous forme de chaîne.

| Nom du test     | Paramètre cube | numTasks | Temps moyen | Prédiction sur une ligne (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | 1        | 91,0725      | 9,959204                        |
|               |                | 4        | 44,09        | 9,959204                        |
|               | `cube = T`     | 1        | 21,1125      | 9,959204                        |
|               |                | 4        | 8.08         | 9,959204                        |

**Conclusions**

L’utilisation de l’argument du paramètre cube améliore nettement les performances.

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>Effet du remplacement des modèles maxDepth par des modèles rxDTree

Dans cette expérience, l’algorithme `rxDTree` a été utilisé pour créer un modèle sur la table *airlineColumnar*. Pour ce test, *numTasks* a été défini sur 4. *maxDepth* a été utilisé avec plusieurs valeurs différentes pour montrer comment l’altération de la profondeur d’arborescence affecte le temps d’exécution.

| Nom du test       | maxDepth | Temps moyen |
|-----------------|----------|--------------|
| TreeDepthEffect | 1        | 10,1975      |
|                 | 2        | 13,2575      |
|                 | 4        | 19,27        |
|                 | 8        | 45,5775      |
|                 | 16       | 339,54       |

**Conclusions**

À mesure que la profondeur de l’arborescence augmente, le nombre total de nœuds augmente de façon exponentielle. Le temps écoulé pour créer le modèle a également augmenté de manière significative.

### <a name="prediction-on-a-stored-model"></a>Prédiction sur un modèle stocké

L’objectif de ce test consistait à déterminer l’impact des performances sur le scoring lorsque le modèle formé est enregistré dans une table SQL Server plutôt que généré dans le cadre du code en cours d’exécution. Pour le scoring, le modèle stocké est chargé à partir de la base de données, et des prédictions sont créées à l’aide d’une trame de données d’une ligne en mémoire (contexte de calcul local).

Les résultats de tests indiquent le temps d’enregistrement du modèle, et le temps de chargement du modèle et de prédiction.

| Nom de la table | Nom du test | Temps moyen d’apprentissage du modèle | Temps pour enregistrer/charger le modèle|
|------------|------------|------------|------------|
| ligne aérienne    | SaveModel| 21,59| 2.08|
| ligne aérienne    | LoadModelAndPredict | | 2,09 (inclut le temps de prédiction) |

**Conclusions**

Le chargement d’un modèle formé à partir d’une table est clairement un moyen plus rapide pour effectuer une prédiction. Nous vous recommandons d’éviter de créer le modèle et de procéder au scoring dans le même script.

## <a name="case-study-optimization-for-the-resume-matching-task"></a>Étude de cas : Optimisation de la tâche de reprise-correspondance

Le modèle de reprise-correspondance a été développé par Ke Huang, scientifique des données de Microsoft, pour tester les performances du code R dans SQL Server et ainsi permettre aux scientifiques des données de créer des solutions professionnelles et évolutives.

### <a name="methods"></a>Méthodes

Les packages RevoScaleR et MicrosoftML ont été utilisés pour former un modèle prédictif dans une solution R complexe impliquant des jeux de données volumineux. Les requêtes SQL et le code R étaient identiques dans tous les tests. Des tests ont été effectués sur une seule machine virtuelle Azure avec SQL Server installé. L’auteur a ensuite comparé les temps de scoring avec et sans les optimisations suivantes fournies par SQL Server :

- Tables en mémoire
- Soft-NUMA
- gouverneur de ressources

Pour évaluer l’effet de soft-NUMA sur l’exécution de scripts R, l’équipe de science des données a testé la solution sur une machine virtuelle Azure avec 20 cœurs physiques. Sur ces cœurs physiques, quatre nœuds soft-NUMA ont été créés automatiquement, chacun contenant cinq cœurs.

Le processus pour affinitiser l’UC a été appliqué dans le scénario reprise-correspondance pour évaluer l’impact sur les travaux R. Quatre **pools de ressources SQL** et quatre **pools de ressources externes** ont été créés, et l’affinité de l’UC a été spécifiée pour garantir que le même ensemble d’UC serait utilisé dans chaque nœud.

Chacun des pools de ressources a été attribué à un autre groupe de charge de travail, afin d’optimiser l’utilisation du matériel. Cela est dû au fait que Soft-NUMA et l’affinité de l’UC ne peuvent pas diviser la mémoire physique des nœuds NUMA physiques ; par conséquent, tous les nœuds Soft-NUMA qui sont par définition basés sur le même nœud NUMA physique doivent utiliser la mémoire dans le même bloc de mémoire du système d’exploitation. En d’autres termes, il n’y a pas d’affinité entre la mémoire et le processeur.

Le processus suivant a été utilisé pour créer cette configuration :

1. Réduire la quantité de mémoire allouée par défaut à SQL Server.

2. Créer quatre pools pour exécuter les travaux R en parallèle.

3. Créer quatre groupes de charge de travail de sorte que chacun d’entre eux soit associé à un pool de ressources.

4. Redémarrer Resource Governor avec les nouveaux groupes de charge de travail et affectations.

5. Créer une fonction classifieur définie par l’utilisateur pour affecter différentes tâches à différents groupes de charge de travail.

6. Mettre à jour la configuration de Resource Governor pour utiliser la fonction pour les groupes de charge de travail appropriés.

### <a name="results"></a>Résultats

La configuration permettant d’obtenir les meilleures performances dans l’étude sur la reprise-correspondance était la suivante :

-   Quatre pools de ressources internes (pour SQL Server)

-   Quatre pools de ressources externes (pour les travaux de script externes)

-   Chaque pool de ressources est associé à un groupe de charge de travail spécifique

-   Chaque pool de ressources est affecté à différentes UC

-   Utilisation maximale de la mémoire interne (pour SQL Server) = 30 %

-   Mémoire maximale pour une utilisation par les sessions R = 70 %

Pour le modèle de reprise-correspondance, l’utilisation de script externe était compliquée et aucun autre service de moteur de base de données n’était en cours d’exécution. Par conséquent, les ressources allouées aux scripts externes ont augmenté jusqu’à 70 %, prouvant ainsi la meilleure configuration pour les performances de script.

Cette configuration a été obtenue en testant différentes valeurs. Si vous utilisez un autre matériel ou solution, la configuration optimale peut différer. Procédez toujours à de nombreux tests pour trouver la meilleure configuration en fonction de votre scénario.

Dans la solution optimisée, 1,1 million lignes de données (avec 100 caractéristiques) ont fait l’objet d’un scoring en moins de 8,5 secondes sur un ordinateur de 20 cœurs. Les optimisations ont considérablement amélioré les performances en termes de temps de scoring.

Les résultats ont également suggéré que le **nombre de caractéristiques** avait un impact significatif sur le temps de scoring. L’amélioration était encore plus évidente lorsque davantage de caractéristiques étaient utilisées dans le modèle de prédiction.

Nous vous recommandons de lire l’article de blog suivant et le didacticiel qui l’accompagne pour en savoir plus.

-   [Optimization tips and tricks for machine learning in SQL Server](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/) (Conseils et astuces d’optimisation pour l’apprentissage automatique dans SQL Server)

De nombreux utilisateurs ont remarqué qu’il y avait une courte pause au moment où le runtime R (ou Python) est chargé pour la première fois. Comme nous l’avons vu dans ces tests, c’est pour cette raison que le temps de la première exécution est souvent mesuré, puis ignoré par la suite. La mise en cache qui suit peut conduire à des différences de performances notables entre la première et la seconde exécutions. Le temps d’exécution peut également être plus important lorsque les données sont déplacées entre SQL Server et le runtime externe, et plus particulièrement sir les données sont transmises sur le réseau plutôt que chargées directement à partir de SQL Server.

Pour toutes ces raisons, il n’existe pas de solution unique pour réduire ce temps de chargement initial, car l’impact sur les performances varie considérablement en fonction de la tâche. Par exemple, la mise en cache est effectuée par lots pour le scoring à une seule ligne ; par conséquent, les opérations de scoring consécutives sont beaucoup plus rapides et ni le modèle, ni le runtime R ne sont pas rechargés. Vous pouvez également utiliser le [scoring natif](../predictions/native-scoring-predict-transact-sql.md) pour éviter le chargement complet du runtime R.

Pour la formation de modèles volumineux ou le scoring dans des lots de grande taille, l’augmentation du temps d’exécution peut être minime par rapport aux avantages obtenus en évitant le déplacement des données ou la diffusion en continu et le traitement en parallèle. Consultez ce billet de blog pour obtenir des conseils supplémentaires en matière de performances :

+ [Using R to detect fraud at 1 million transactions per second](https://blog.revolutionanalytics.com/2016/09/fraud-detection.html/) (Utilisation de R pour détecter les fraudes en traitant 1 million de transactions par seconde)

## <a name="resources"></a>Ressources

Vous trouverez ci-dessous des liens vers des informations, des outils et des scripts utilisés pour le développement de ces tests.

+ Scripts de test de performances et liens vers les données : [Exemple de données et de scripts pour l’étude des optimisations de SQL Server](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Article décrivant la solution de reprise-correspondance : [Optimization tip and tricks for SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/) (Conseils et astuces d’optimisation pour SQL Server R Services)

+ Scripts utilisés dans l’optimisation SQL pour la solution de reprise-correspondance : [Référentiel GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips-Resume-Matching)

### <a name="learn-about-windows-server-management"></a>En savoir plus sur la gestion de serveur Windows

+ [Comment faire pour déterminer la taille de fichier d’échange appropriée pour les versions 64 bits de Windows](https://support.microsoft.com/kb/2860880)

+ [Présentation de l’accès NUMA](https://technet.microsoft.com/library/ms178144.aspx)

+ [Prise en charge de la technologie NUMA dans SQL Server](https://technet.microsoft.com/library/ms180954.aspx)

+ [Soft-NUMA (SQL Server)](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>En savoir plus sur les optimisations de SQL Server

+ [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

+ [Introduction aux tables optimisées en mémoire](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ La [Démonstration : Optimisation des performances de l’OLTP en mémoire](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [Compression des données](../../relational-databases/data-compression/data-compression.md)

+ [Activer la compression sur une table ou un index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Désactiver la compression sur une table ou un index](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>En savoir plus sur la gestion SQL Server

+ [Surveillance et réglage des performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)

+ [Présentation de Resource Governor](https://technet.microsoft.com/library/bb895232.aspx)

+ [An example of configuring Resource Governor](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/) (Un exemple de configuration de Resource Governor)

### <a name="tools"></a>Outils

+ [Générateur de charge de stockage/outil de test de performances DISKSPD](https://github.com/microsoft/diskspd)

+ [Informations de référence sur l’utilitaire FSUtil](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>Autres articles de cette série

[Optimisation des performances pour R - Introduction](sql-server-r-services-performance-tuning.md)

[Optimisation des performances pour R - Configuration de SQL Server](sql-server-configuration-r-services.md)

[Optimisation des performances pour R - Code R et optimisation des données](r-and-data-optimization-r-services.md)

[Optimisation des performances pour R - Résultats de l’étude de cas](performance-case-study-r-services.md)
