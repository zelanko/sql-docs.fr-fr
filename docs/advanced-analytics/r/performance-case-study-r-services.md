---
title: Performances pour les SQL Server R Services-résultats et les ressources
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: aa56a9367271df2172236b133d85b5771089b1ac
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715044"
---
# <a name="performance-for-r-services-results-and-resources"></a>Performances pour R services: résultats et ressources
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article est le quatrième et le dernier d’une série qui décrit l’optimisation des performances pour R services. Cet article résume les méthodes, les conclusions et les conclusions de deux études de cas qui ont testé diverses méthodes d’optimisation.

Les deux études de cas ont des objectifs différents:

+ La première étude de cas, par l’équipe de développement R services, a cherché à mesurer l’impact des techniques d’optimisation spécifiques
+ La deuxième étude de cas, par une équipe de scientifiques des données, a expérimenté plusieurs méthodes pour déterminer les meilleures optimisations pour un scénario de notation de volume élevé spécifique.

Cette rubrique répertorie les résultats détaillés de la première étude de cas. Pour la deuxième étude de cas, un résumé décrit les résultats globaux. À la fin de cette rubrique se trouvent des liens vers tous les scripts et exemples de données, ainsi que des ressources utilisées par les auteurs d’origine.

## <a name="performance-case-study-airline-dataset"></a>Étude de cas sur les performances: Jeu de données d’une compagnie aérienne

Cette étude de cas par l’équipe de développement SQL Server R Services a testé les effets de différentes optimisations. Un modèle rxLogit unique a été créé et le score est réalisé sur le jeu de données de la compagnie aérienne. Les optimisations ont été appliquées pendant les processus d’apprentissage et de notation pour évaluer les impacts individuels.

- GitHub [Exemple de données et de scripts](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning) pour l’étude des optimisations de SQL Server

### <a name="test-methods"></a>Méthodes de test

1. Le jeu de données de la compagnie aérienne est constitué d’une seule table de 10 millions de lignes. Il a été téléchargé et chargé en bloc dans SQL Server.
2. Six copies de la table ont été effectuées.
3. Diverses modifications ont été appliquées aux copies de la table, afin de tester SQL Server fonctionnalités telles que la compression de page, la compression de ligne, l’indexation, le magasin de données en colonnes, etc.
4. Les performances ont été mesurées avant et après l’application de chaque optimisation.

| Nom de la table| Description|
|------|------|
| *airline* | Données converties à partir du fichier xdf d’origine à l’aide de `rxDataStep`|                          |
| *airlineWithIntCol*   | Chaîne *DayOfWeek* convertie en entier. Colonne *rowNum* également ajoutée.|
| *airlineWithIndex*    | Mêmes données que dans la table *airlineWithIntCol*, mais avec un seul index cluster utilisant la colonne *rowNum*.|
| *airlineWithPageComp* | Mêmes données que dans la table *airlineWithIndex*, mais avec la compression de page activée. Deux colonnes également ajoutées, *CRSDepHour* et *Late*, qui sont calculées à partir de *CRSDepTime* et *ArrDelay*. |
| *airlineWithRowComp*  | Mêmes données que dans la table *airlineWithIndex*, mais avec la compression de ligne activée. Deux colonnes également ajoutées, *CRSDepHour* et *Late*, qui sont calculées à partir de *CRSDepTime* et *ArrDelay*. |
| *airlineColumnar*     | Stockage en colonnes avec un seul index cluster. Table remplie avec les données d’un fichier csv nettoyé.|

Chaque test consistait à suivre les étapes suivantes:

1. Une opération garbage collection R a été induite avant chaque test.
2. Un modèle de régression logistique a été créé en fonction des données de la table. La valeur de *rowsPerRead* a été définie sur 500 000 pour chaque test.
3. Les scores ont été générés à l’aide du modèle formé
4. Chaque test a été exécuté six fois. L’heure de la première exécution («exécution à froid») a été supprimée. Pour autoriser les valeurs hors norme occasionnelles, le délai **maximal** entre les cinq exécutions restantes a également été supprimé. Le temps d’exécution écoulé moyen de chaque test a été calculé à partir de la moyenne des quatre exécutions restantes.
5. Les tests ont été exécutés à l’aide du paramètre *reportProgress* avec la valeur 3 (= minutage et progression des rapports). Chaque fichier de sortie contient des informations sur le temps passé dans les e/s, le temps de transition et le temps de calcul. Ces informations sont utiles pour le diagnostic et la résolution des problèmes.
6. La sortie de la console était également dirigée vers un fichier dans le répertoire de sortie.
7. Les scripts de test ont traité les temps de ces fichiers pour calculer la durée moyenne des exécutions.

Par exemple, les résultats suivants sont les heures d’un test unique. Les valeurs les plus intéressantes sont **Total read time** (le temps d’E/S) et **Transition time** (le temps passé à créer les processus de calcul).

**Exemples de minutages**

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

Nous vous recommandons de télécharger et de modifier les scripts de test pour vous aider à résoudre les problèmes liés à R services ou aux fonctions RevoScaleR.

### <a name="test-results-all"></a>Résultats des tests (tous)

Cette section compare les résultats avant et après pour chacun des tests.

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>Taille des données avec compression et magasin de tables en colonnes

Le premier test a comparé l’utilisation de la compression et d’une table en colonnes pour réduire la taille des données.

| Nom de la table            | Lignes     | Réservé   | Données       | index_size | Inutilisé  | % gagné (réservé) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10 000 000 | 2 978 816 Ko | 2 972 160 Ko | 6 128 Ko    | 528 Ko  | 0                   |
| *airlineWithPageComp* | 10 000 000 | 625 784 Ko  | 623 744 Ko  | 1 352 Ko    | 688 Ko  | 79 %                 |
| *airlineWithRowComp*  | 10 000 000 | 1 262 520 KB | 1 258 880 Ko | 2 552 Ko    | 1 088 Ko | 58 %                 |
| *airlineColumnar*     | 9 999 999  | 201 992 Ko  | 201 624 Ko  | n/a        | 368 Ko  | 93 %                 |

**Conclusions**

La plus grande réduction de la taille des données a été obtenue en appliquant un index ColumnStore, suivi de la compression de page.

#### <a name="effects-of-compression"></a>Effets de la compression

Ce test compare les avantages de la compression de ligne, la compression de page et aucune compression. Un modèle a été formé `rxLinMod` à l’aide des données de trois tables de données différentes. La même formule et requête a été utilisée pour toutes les tables.

| Nom de la table            | Nom du test       | numTasks | Temps moyen |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | 1        | 5,6775       |
|                       | NoCompression-parallèle| 4        | 5,1775       |
| *airlineWithPageComp* | PageCompression | 1        | 6,7875       |
|                       | PageCompression-parallèle | 4        | 5,3225       |
| *airlineWithRowComp*  | RowCompression  | 1        | 6,1325       |
|                       | RowCompression-parallèle  | 4        | 5,2375       |

**Conclusions**

La compression seule ne semble pas être utile. Dans cet exemple, l’augmentation du processeur pour gérer la compression compense la diminution du temps d’e/s.

Toutefois, quand le test est exécuté en parallèle en définissant *numTasks* sur 4, le temps moyen diminue.

L’effet de la compression peut être plus significatif pour les jeux de données volumineux. La compression varie selon le jeu de données et les valeurs. Vous avez donc intérêt à faire plusieurs tests pour évaluer l’effet de la compression sur votre jeu de données.

### <a name="effect-of-windows-power-plan-options"></a>Effet des options du mode de gestion de l’alimentation Windows

Dans cette expérience, `rxLinMod` a été utilisé avec la table *airlineWithIntCol*. Le mode de gestion de l’alimentation Windows a été défini sur des performances équilibrées ou **élevées**. Pour tous les tests, *numTasks* a été défini sur 1. Le test a été exécuté six fois et a été exécuté deux fois sous les deux options d’alimentation pour analyser la variabilité des résultats.

Option de puissance **haute performance** :

| Nom du test | Exécutez \# | Temps écoulé | Temps moyen |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,57 secondes |              |
|           | 2      | 3,45 secondes |              |
|           | 3      | 3,45 secondes |              |
|           | 4      | 3,55 secondes |              |
|           | 5\.      | 3,55 secondes |              |
|           | 6\.      | 3,45 secondes |              |
|           |        |              | 3,475        |
|           | 1      | 3,45 secondes |              |
|           | 2      | 3,53 secondes |              |
|           | 3      | 3,63 secondes |              |
|           | 4      | 3,49 secondes |              |
|           | 5\.      | 3,54 secondes |              |
|           | 6\.      | 3,47 secondes |              |
|           |        |              | 3,5075       |

Option de gestion de l’alimentation **Équilibré** :

| Nom du test | Exécutez \# | Temps écoulé | Temps moyen |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,89 secondes |              |
|           | 2      | 4,15 secondes |              |
|           | 3      | 3,77 secondes |              |
|           | 4      | 5 secondes    |              |
|           | 5\.      | 3,92 secondes |              |
|           | 6\.      | 3,8 secondes  |              |
|           |        |              | 3,91         |
|           | 1      | 3,82 secondes |              |
|           | 2      | 3,84 secondes |              |
|           | 3      | 3,86 secondes |              |
|           | 4      | 4,07 secondes |              |
|           | 5\.      | 4,86 secondes |              |
|           | 6\.      | 3,75 secondes |              |
|           |        |              | 3,88         |

**Conclusions**

La durée d’exécution est plus cohérente et plus rapide lors de l’utilisation du mode de gestion de l’alimentation **hautes performances** de Windows.

#### <a name="using-integer-vs-strings-in-formulas"></a>Utilisation d’entiers et de chaînes dans les formules

Ce test a évalué l’impact de la modification du code R afin d’éviter un problème courant avec les facteurs de chaîne. Plus précisément, un modèle a été `rxLinMod` formé à l’aide de deux tables: dans le premier, les facteurs sont stockés sous forme de chaînes. dans la seconde table, les facteurs sont stockés sous forme d’entiers.

+ Pour la table de la *compagnie aérienne* , la colonne [DayOfWeek] contient des chaînes. Le paramètre _colInfo_ a été utilisé pour spécifier les niveaux de facteur (lundi, mardi,...)

+  Pour la table *airlineWithIndex* , [DayOfWeek] est un entier. Le paramètre _colInfo_ n’a pas été spécifié.

+ Dans les deux cas, la même formule a été utilisée : `ArrDelay ~ CRSDepTime + DayOfWeek`.

| Nom de la table          | Nom du test   | Temps moyen |
|---------------------|-------------|--------------|
| *Compagnies aériennes*           | *FactorCol* | 10,72        |
| *airlineWithIntCol* | *IntCol*    | 3,4475       |

**Conclusions**

L’utilisation de nombres entiers plutôt que de chaînes pour les facteurs présente un avantage évident.

### <a name="avoiding-transformation-functions"></a>Prévention des fonctions de transformation

Dans ce test, un modèle a été formé `rxLinMod`à l’aide de, mais le code a été modifié entre les deux exécutions:

+ Lors de la première exécution, une fonction de transformation a été appliquée dans le cadre de la génération du modèle. 
+ Dans la deuxième exécution, les valeurs de fonctionnalité étaient précalculées et disponibles, afin qu’aucune fonction de transformation ne soit requise.

| Nom du test             | Temps moyen |
|-----------------------|--------------|
| WithTransformation    | 5,1675       |
| WithoutTransformation | 4,7          |

**Conclusions**

Le temps de formation était plus petit quand vous **n’utilisez pas** de fonction de transformation. En d’autres termes, le modèle a été formé plus rapidement lors de l’utilisation de colonnes qui sont précalculées et conservées dans la table.

Les économies sont supposées être supérieures si le nombre de transformations et le jeu de données étaient plus élevés\> (100 millions).

### <a name="using-columnar-store"></a>Utilisation du magasin en colonnes

Ce test a évalué les avantages en matière de performances de l’utilisation d’un magasin de données et d’un index en colonnes. Le même modèle a été formé `rxLinMod` avec et aucune transformation de données.

+ Lors de la première exécution, la table de données utilisait un magasin de lignes standard.
+ Dans la deuxième exécution, une banque de colonnes a été utilisée.

| Nom de la table         | Nom du test | Temps moyen |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4,67         |
| *airlineColumnar*  | ColStore  | 4,555        |

**Conclusions**

Les performances sont meilleures avec le magasin en colonnes qu’avec le magasin de lignes standard. Une différence significative en matière de performances peut se produire sur des jeux\> de données plus volumineux (100 M).

### <a name="effect-of-using-the-cube-parameter"></a>Effet de l’utilisation du paramètre cube

L’objectif de ce test consistait à déterminer si l’option dans RevoScaleR pour l’utilisation du paramètre de **cube** precalculé peut améliorer les performances. Un modèle a été formé `rxLinMod`à l’aide de, à l’aide de la formule suivante:

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

Dans le tableau, les facteurs *DayOfWeek* sont stockés sous forme de chaîne.

| Nom du test     | Paramètre cube | numTasks | Temps moyen | Prédiction de ligne simple (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | 1        | 91,0725      | 9,959204                        |
|               |                | 4        | 44,09        | 9,959204                        |
|               | `cube = T`     | 1        | 21,1125      | 9,959204                        |
|               |                | 4        | 8,08         | 9,959204                        |

**Conclusions**

L’utilisation de l’argument de paramètre de cube améliore nettement les performances.

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>Effet de la modification de maxDepth pour les modèles rxDTree

Dans cette expérience, l' `rxDTree` algorithme a été utilisé pour créer un modèle sur la table *airlineColumnar* . Pour ce test, *numTasks* a été défini sur 4. Plusieurs valeurs différentes pour *maxdepth* ont été utilisées pour illustrer la façon dont la modification de la profondeur de l’arborescence affecte le temps d’exécution.

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

L’objectif de ce test consistait à déterminer l’impact sur les performances de la notation lorsque le modèle formé est enregistré dans une table SQL Server plutôt que d’être généré dans le cadre du code en cours d’exécution. Pour la notation, le modèle stocké est chargé à partir de la base de données et les prédictions sont créées à l’aide d’une trame de données d’une ligne en mémoire (contexte de calcul local).

Les résultats des tests indiquent l’heure d’enregistrement du modèle et le temps nécessaire pour charger le modèle et prédire.

| Nom de la table | Nom du test | Temps moyen d’apprentissage du modèle | Temps pour enregistrer/charger le modèle|
|------------|------------|------------|------------|
| airline    | SaveModel| 21,59| 2,08|
| airline    | LoadModelAndPredict | | 2,09 (inclut le temps de prédiction) |

**Conclusions**

Le chargement d’un modèle formé à partir d’une table est clairement un moyen plus rapide d’effectuer une prédiction. Nous vous recommandons d’éviter de créer le modèle et d’effectuer le score All dans le même script.

## <a name="case-study-optimization-for-the-resume-matching-task"></a>Étude de cas: Optimisation de la tâche de reprise correspondante

Le modèle de mise en correspondance des CV a été développé par Microsoft Data science ke Huang pour tester les performances du code R dans SQL Server, ce qui permet aux scientifiques des données de créer des solutions évolutives à l’échelle de l’entreprise.

### <a name="methods"></a>Méthodes

Les packages RevoScaleR et MicrosoftML ont été utilisés pour l’apprentissage d’un modèle prédictif dans une solution R complexe impliquant des jeux de données volumineux. Les requêtes SQL et le code R étaient identiques dans tous les tests. Des tests ont été effectués sur une seule machine virtuelle Azure avec SQL Server installé. L’auteur a ensuite comparé les durées de notation avec et sans les optimisations suivantes fournies par SQL Server:

- Tables en mémoire
- Soft-NUMA
- gouverneur de ressources

Pour évaluer l’effet de soft-NUMA sur l’exécution de scripts R, l’équipe de science des données a testé la solution sur une machine virtuelle Azure avec 20 cœurs physiques. Sur ces cœurs physiques, quatre nœuds soft-NUMA ont été créés automatiquement, de sorte que chaque nœud contenait cinq cœurs.

Le affinitization de l’UC a été appliqué dans le scénario de reprise, pour évaluer l’impact sur les travaux R. Quatre **pools de ressources SQL** et quatre pools de **ressources externes** ont été créés, et l’affinité du processeur a été spécifiée pour garantir que le même ensemble de processeurs serait utilisé dans chaque nœud.

Chacun des pools de ressources a été attribué à un autre groupe de charge de travail, afin d’optimiser l’utilisation du matériel. Cela est dû au fait que soft-NUMA et l’affinité du processeur ne peuvent pas diviser la mémoire physique des nœuds NUMA physiques; par conséquent, par définition, tous les nœuds NUMA conditionnels basés sur le même nœud NUMA physique doivent utiliser la mémoire dans le même bloc de mémoire du système d’exploitation. En d’autres termes, il n’y a pas d’affinité entre la mémoire et le processeur.

Le processus suivant a été utilisé pour créer cette configuration:

1. Réduisez la quantité de mémoire allouée par défaut à SQL Server.

2. Créez quatre nouveaux pools pour exécuter les travaux R en parallèle.

3. Créez quatre groupes de charges de travail de sorte que chaque groupe de charges de travail soit associé à un pool de ressources.

4. Redémarrez Resource Governor avec les nouvelles affectations et groupes de charge de travail.

5. Créer une fonction classifieur définie par l’utilisateur (UDF) pour affecter des tâches différentes à différents groupes de charge de travail.

6. Mettez à jour la configuration de Resource Governor pour utiliser la fonction pour les groupes de charge de travail appropriés.

### <a name="results"></a>Résultats

La configuration qui avait les meilleures performances dans l’étude de la reprise correspondante était la suivante:

-   Quatre pools de ressources internes (par SQL Server)

-   Quatre pools de ressources externes (pour les tâches de script externes)

-   Chaque pool de ressources est associé à un groupe de charges de travail spécifique

-   Chaque pool de ressources est affecté à différents processeurs

-   Utilisation maximale de la mémoire interne (pour SQL Server) = 30%

-   Mémoire maximale pour une utilisation par les sessions R = 70%

Pour le modèle de correspondance de reprise, l’utilisation de script externe était lourde et aucun autre service de moteur de base de données n’était en cours d’exécution. Par conséquent, les ressources allouées aux scripts externes ont été augmentées à 70%, ce qui a démontré la meilleure configuration pour les performances des scripts.

Cette configuration a été effectuée à l’aide de différentes valeurs. Si vous utilisez un matériel différent ou une autre solution, la configuration optimale peut être différente. Faites toujours des essais pour trouver la configuration la mieux adaptée à votre cas.

Dans la solution optimisée, 1,1 million lignes de données (avec 100 fonctionnalités) ont été évaluées en moins de 8,5 secondes sur un ordinateur de 20 cœurs. Les optimisations ont considérablement amélioré les performances en termes de temps de score.

Les résultats ont également suggéré que le **nombre de fonctionnalités** avait un impact significatif sur la durée de la notation. L’amélioration est encore plus évidente lorsque davantage de fonctionnalités étaient utilisées dans le modèle de prédiction.

Nous vous recommandons de lire cet article de blog et le didacticiel qui l’accompagne pour une discussion détaillée.

-   [Conseils et astuces d’optimisation pour Machine Learning dans SQL Server](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

De nombreux utilisateurs ont noté qu’il y a une petite pause, car le runtime R (ou python) est chargé pour la première fois. Pour cette raison, comme décrit dans ces tests, l’heure de la première exécution est souvent mesurée, mais ignorée par la suite. La mise en cache suivante peut entraîner des différences de performances notables entre la première et la deuxième exécution. Il y a également une certaine charge lorsque les données sont déplacées entre SQL Server et le runtime externe, en particulier si les données sont transmises sur le réseau au lieu d’être chargées directement à partir de SQL Server.

Pour toutes ces raisons, il n’existe pas de solution unique pour atténuer ce temps de chargement initial, car l’impact sur les performances varie considérablement en fonction de la tâche. Par exemple, la mise en cache est effectuée pour un score à une seule ligne dans les lots; par conséquent, les opérations de notation consécutives sont beaucoup plus rapides et le modèle et le runtime R ne sont pas rechargés. Vous pouvez également utiliser le [score natif](../sql-native-scoring.md) pour éviter le chargement intégral du runtime R.

Pour l’apprentissage de modèles volumineux ou le calcul de score dans de grands lots, la surcharge peut être minime par rapport aux gains résultants de l’évitement du déplacement des données ou de la diffusion en continu et du traitement parallèle. Consultez ce billet de blog pour obtenir des conseils supplémentaires en matière de performances:

+ [Utilisation de R pour détecter les fraudes à 1 million transactions par seconde](https://blog.revolutionanalytics.com/2016/09/fraud-detection.html/)

## <a name="resources"></a>Ressources

Vous trouverez ci-dessous des liens vers des informations, des outils et des scripts utilisés dans le développement de ces tests.

+ Scripts de test de performances et liens vers les données: [Exemple de données et de scripts pour l’étude des optimisations de SQL Server](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Article décrivant la solution de reprise de correspondance: [Conseil et astuces d’optimisation pour SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

+ Scripts utilisés dans l’optimisation SQL pour la solution de reprise correspondante: [Dépôt GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)

### <a name="learn-about-windows-server-management"></a>En savoir plus sur la gestion de Windows Server

+ [Comment faire pour déterminer la taille de fichier d’échange appropriée pour les versions 64 bits de Windows](https://support.microsoft.com/kb/2860880)

+ [Fonctionnement de NUMA](https://technet.microsoft.com/library/ms178144.aspx)

+ [Comment SQL Server prend en charge NUMA](https://technet.microsoft.com/library/ms180954.aspx)

+ [NUMA Soft](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>En savoir plus sur les optimisations de SQL Server

+ [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

+ [Présentation des tables optimisées en mémoire](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ La [Démonstration : Amélioration des performances de l’OLTP en mémoire](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [Compression des données](../../relational-databases/data-compression/data-compression.md)

+ [Activer la compression sur une table ou un index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Désactiver la compression sur une table ou un index](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>En savoir plus sur la gestion des SQL Server

+ [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)

+ [Présentation de Resource Governor](https://technet.microsoft.com/library/bb895232.aspx)

+ [Gouvernance des ressources pour R Services](resource-governance-for-r-services.md)

+ [Comment créer un pool de ressources pour R](how-to-create-a-resource-pool-for-r.md)

+ [Exemple de configuration de Resource Governor](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/)

### <a name="tools"></a>Outils

+ [Générateur de charge de stockage/outil de test de performances DISKSPD](https://github.com/microsoft/diskspd)

+ [Informations de référence sur l’utilitaire FSUtil](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>Autres Articles de cette série

[Réglage des performances pour R-introduction](sql-server-r-services-performance-tuning.md)

[Réglage des performances pour la configuration de R-SQL Server](sql-server-configuration-r-services.md)

[Réglage des performances pour le code R-R et l’optimisation des données](r-and-data-optimization-r-services.md)

[Réglage des performances-résultats de l’étude de cas](performance-case-study-r-services.md)
