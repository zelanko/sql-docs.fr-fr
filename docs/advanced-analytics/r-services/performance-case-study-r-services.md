---
title: "&#201;tude de cas de performances (R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e902312-ad9c-480d-b82f-b871cd1052d9
caps.latest.revision: 8
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 6
---
# &#201;tude de cas de performances (R Services)

Pour illustrer l’effet de l’aide fournie dans les sections précédentes, les tests ont été exécutés à l’aide de tables de l’ensemble de données compagnie aérienne. 

## Tests et des exemples de données

Il existe six tables avec les lignes de 10M de chaque table :

| Nom de table |  Description |
| ---------- | ----------- |
| _compagnie aérienne_ | Données converties à partir de l’utilisation de fichier d’origine xdf *rxDataStep*. |
| _airlineWithIntCol_ | *DayOfWeek* converti en un entier plutôt qu’une chaîne. Ajoute également un *rowNum* colonne. |
| _airlineWithIndex_ | Les mêmes données que le *airlineWithIntCol* table, mais avec un seul index en cluster à l’aide du *rowNum* colonne. |
| _airlineWithPageComp_ | Les mêmes données que le *airlineWithIndex* table, mais avec la compression de page est activé. Ajoute également deux colonnes, *CRSDepHour* et *en retard*, qui sont calculé à partir de *CRSDepTime* et *ArrDelay*. |
| _airlineWithRowComp_ | Les mêmes données que le *airlineWithIndex* table, mais avec la compression de ligne est activé. Ajoute également deux colonnes, *CRSDepHour* et *en retard* qui sont calculé à partir de *CRSDepTime* et *ArrDelay*. 
| _airlineColumnar_ | Un magasin de colonnes avec un index cluster unique. Cette table est remplie avec les données d’un fichier csv nettoyé de fichier. |

Les scripts utilisés pour effectuer les tests décrits dans cette section, ainsi que des liens vers les exemples de données utilisés pour les tests, sont disponibles au [https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning).

Chaque test a été exécutée six fois, l’heure de la première exécution (exécuter, de froid) a été supprimé. Pour autoriser les valeurs aberrantes occasionnelles, la durée maximale de l’exécution de cinq autres a été également supprimée. La moyenne des quatre séries restants a été effectuée pour calculer l’exécution écoulée moyen de chaque test. R garbage collection a été induit avant chaque test. La valeur de *rowsPerRead* de chaque test a été défini sur 500000.

## Taille des données lors de l’utilisation de la Compression et une Table de stockage en colonnes

Voici les résultats de l’utilisation de la compression et une table en colonnes afin de réduire la taille des données :

| Nom de table | Lignes | Réservé | Data | index_size | Inutilisé | % De l’enregistrement (réservé) |
| ---------- | ---- | -------- | ---- | ---------- | ------ | ------------------- |
| airlineWithIndex | 10000000 | 2978816 KO | 2972160 KO | 6128 KO | 528 KO | 0 |
| airlineWithPageComp | 10000000 | 625784 KO | 623744 KO | 1352 KO | 688 KO | 79% |
| airlineWithRowComp | 10000000 | 1262520 KO | 1258880 KO | 2552 KO | 1088 KO | 58% |
| airlineColumnar | 9999999 | 201992 KO | 201624 KO | n/a | 368 KO | 93% |

## À l’aide de Visual Studio entier. Chaîne de formule

Dans cette expérience, `rxLinMod` a été utilisé avec la table de la compagnie aérienne (où *DayOfWeek* est une chaîne) et *airlineWithIndex* (où *DayOfWeek* est un entier). Pour le premier cas, `colInfo` a été utilisé pour spécifier les niveaux de facteur (`Monday`, `Tuesday`, ...). Pour la seconde, `colInfo` n’a été spécifié. Dans les deux cas, la même formule a été utilisée. La formule utilisée est `ArrDelay ~ CRSDepTime + DayOfWeek`. Les résultats suivants illustre clairement l’avantage d’utiliser la chaîne de vs entier :

| Nom de table | Nom du test | Durée moyenne |
| ---------- | --------- | ------------ |
| compagnie aérienne | FactorCol | 10.72 |
| airlineWithIntCol | IntCol | 3.4475 |

## À l’aide de la Compression

Dans cette expérience, `rxLinMod` a été utilisé avec le *airlineWithIndex*, *airlineWithPageComp*, et *airlineWithRowComp* tables. La même formule et requête a été utilisé pour toutes les tables. 

| Nom de table | Nom du test | numTasks | Durée moyenne |
| ---------- | --------- | -------- | ------------ |
| airlineWithIndex | NoCompression |  1 | 5.6775 |
| &nbsp; | &nbsp; | 4 | 5.1775 |
| airlineWithPageComp | PageCompression |  1 | 6.7875 |
| &nbsp; | &nbsp; | 4 | 5.3225 |
| airlineWithRowComp | RowCompression |  1 | 6.1325 |
| &nbsp; | &nbsp; | 4 | 5.2375 |

Notez que seule la compression (*numTasks* définie sur 1) ne semble pas pour vous aider dans cet exemple, comme l’augmentation de l’UC pour gérer la compression permet de compenser la diminution des temps d’e/s. Cependant, lorsque le test est exécuté en parallèle en définissant *numTasks* à 4, la durée moyenne diminue. Pour les grands ensembles de données, l’effet de compression peut être plus visible. La compression varie selon le jeu de données et les valeurs, expérimentation peut être nécessaire pour déterminer la compression de l’effet sur votre jeu de données.

## Éviter la fonction de Transformation

Dans cette expérience, `rxLinMod` est utilisé avec la table airlineWithIndex avec et sans l’aide d’une fonction de transformation.  

| Nom du test | Durée moyenne |
| --------- | ------------ |
| WithTransformation | 5.1675 |
| WithoutTransformation | 4.7 |

Notez qu’il existe une amélioration dans le temps lorsque vous n’utilisez ne pas une fonction de transformation (à l’aide de colonnes précalculée et conservées dans la table). Les économies sera beaucoup plus s’il existe de nombreuses transformations plus et le jeu de données est supérieure (> 100M).

## À l’aide de la banque de colonnes

Dans cette expérience, `rxLinMod` a été utilisé avec les tables airlineWithIndex et airlineColumnar sans transformation. Les résultats indiquent que le magasin de colonnes permettre plus performant que banque de lignes. Il y a une différence significative des performances sur l’ensemble de données plus important (> 100 M).  

| Nom de table | Nom du test |Durée moyenne |
| ---------- | --------- | ------------ |
| airlineWithIndex | RowStore | 4.67 |
| airlineColumnar | ColStore | 4.555 |

## Effet du paramètre de Cube

Dans cette expérience, `rxLinMod` est utilisé avec la table de la compagnie aérienne où `DayOfWeek` est stocké sous forme de chaîne. La formule utilisée est `ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime`. Les résultats indiquent clairement que l’utilisation de `cube` paramètre permet aux performances. 

| Nom du test | Paramètre de cube | numTasks | Durée moyenne | Une ligne prédire (ArrDelay_Pred) |
| --------- | -------------- | -------- | ------------ | ------------------------------- |
| CubeArgEffect | `cube = F` |  1 | 91.0725 | 9.959204 |
| &nbsp; | &nbsp; | 4 | 44.09 | 9.959204 |
| &nbsp; | `cube = T` |  1 | 21.1125 | 9.959204 |
| &nbsp; | &nbsp; | 4 | 8.08 | 9.959204 |

## Effet de maxDepth pour rxDTree

Dans cette expérience, `rxDTree` est utilisé avec la table airlineColumnar. Plusieurs valeurs différentes pour *maxDepth* ont été utilisés pour montrer comment il affecte la complexité de l’exécution. Comme la profondeur augmente, le nombre total de nœuds augmente de façon exponentielle et augmente considérablement le temps écoulé. Pour que ce test *numTasks* a été défini à 4.

| Nom du test | maxDepth | Durée moyenne |
| --------- | -------- | ------------ |
| TreeDepthEffect |  1 | 10.1975 |
| &nbsp; | 2 | 13.2575 |
| &nbsp; | 4 | 19.27 |
| &nbsp; | 8 | 45.5775 |
| &nbsp; | 16 | 339.54 |

## Effet de l’Option de l’alimentation

Dans cette expérience, `rxLinMod` a été utilisé avec la table airlineWithIntCol tandis que Windows a été défini, à l’équilibre ainsi que des performances élevées, options d’alimentation. Pour tous les tests, *numTasks* a été définie sur 1. Le test a été exécuté 6 fois et a été exécutée deux fois dans les deux options d’alimentation pour illustrer la variabilité des résultats lorsque vous utilisez l’option d’alimentation à charge équilibrée. Les résultats montrent que les nombres sont plus cohérent et plus rapides pour l’option de l’alimentation de hautes performances. 

__Hautes performances__ option d’alimentation :

| Nom du test | Exécuter # | Temps écoulé | Durée moyenne |
| --------- | ----- | ------------ | ------------ |
| IntCol |  1 | 3.57 secondes | &nbsp; |
| &nbsp; | 2 | 3,45 secondes | &nbsp; |
| &nbsp; | 3 | 3,45 secondes | &nbsp; |
| &nbsp; | 4 | 3.55 secondes | &nbsp; |
| &nbsp; | 5 | 3.55 secondes | &nbsp; |
| &nbsp; | 6 | 3,45 secondes | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.475 |
| &nbsp; |  1 | 3,45 secondes | &nbsp; |
| &nbsp; | 2 | 3.53 secondes | &nbsp; |
| &nbsp; | 3 | 3,63 secondes | &nbsp; |
| &nbsp; | 4 | 3,49 secondes | &nbsp; |
| &nbsp; | 5 | 3,54 secondes | &nbsp; |
| &nbsp; | 6 | 3.47 secondes | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.5075 |

__Équilibrage__ option d’alimentation :

| Nom du test | Exécuter # | Temps écoulé | Durée moyenne |
| --------- | ----- | ------------ | ------------ |
| IntCol |  1 | 3.89 secondes | &nbsp; |
| &nbsp; | 2 | 4.15 secondes | &nbsp; |
| &nbsp; | 3 | 3.77 secondes | &nbsp; |
| &nbsp; | 4 | 5 secondes | &nbsp; |
| &nbsp; | 5 | 3.92 secondes | &nbsp; |
| &nbsp; | 6 | 3,8 secondes | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.91 |
| &nbsp; |  1 | 3,82 secondes | &nbsp; |
| &nbsp; | 2 | 3,84 secondes | &nbsp; |
| &nbsp; | 3 | 3.86 secondes | &nbsp; |
| &nbsp; | 4 | 4.07 secondes | &nbsp; |
| &nbsp; | 5 | 4,86 secondes | &nbsp; |
| &nbsp; | 6 | 3,75 secondes | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.88 |

## Prédiction à l’aide d’un modèle stocké

Dans cette expérience, un modèle est créé et stocké dans une base de données. Puis le modèle stocké est chargé à partir de la base de données et des prédictions créées à l’aide d’une trame de données d’une ligne dans la mémoire (contexte de calcul local). Le temps nécessaire pour former, enregistrer et charger le modèle et prédire est indiqué ci-dessous. Il s’agit clairement une méthode plus rapide pour réaliser une prédiction. Les résultats des tests affichent l’heure pour enregistrer le modèle et le temps nécessaire pour charger le modèle et à prévoir. 

| Nom de table | Nom du test | Durée moyenne (pour former un modèle) | Temps de modèle de charge et enregistrer |
| ---------- | --------- | ----- | ----- |
| compagnie aérienne | SaveModel | 21.59 | 2.08 | 
| &nbsp; | LoadModelAndPredict | &nbsp; |  2.09 (inclut le temps à prédire) |


## Résolution des problèmes de performances

Les tests utilisés dans cette section produisent des fichiers de sortie pour chaque série à l’aide de la *reportProgress* paramètre, qui est transmise aux tests avec la valeur `3`. La sortie de console est dirigée vers un fichier dans le répertoire de sortie. Le fichier de sortie contient des informations concernant le temps consacré aux e/s, durée de transition et des temps de calcul. Ces heures sont utiles pour le dépannage et de diagnostic. Les scripts de test traitent ces heures pour les séries différentes trouver le temps moyen sur s’exécute. Ces scripts de test et techniques peuvent également être utiles pour résoudre les problèmes à l’aide des fonctions analytiques rx votre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Par exemple, le code suivant les temps échantillon pour une exécution. Le minutage d’intérêt principal est Total de lecture d’e/s (heure) et passer du temps (temps de configuration de processus pour le calcul).

    Running IntCol Test. Using airlineWithIntCol table.  
        run  1  took  3.66  seconds  
        run  2  took  3.44  seconds  
        run  3  took  3.44  seconds  
        run  4  took  3.44  seconds  
        run  5  took  3.45  seconds  
        run  6  took  3.75  seconds  

    Average Time:  3.4425  
                    metric   time    pct 
    1           Total time 3.4425 100.00 
    2 Overall compute time 2.8512  82.82 
    3      Total read time 2.5378  73.72 
    4      Transition time 0.5913  17.18 
    5    Total non IO time 0.3134   9.10 
 
 ## Voir aussi
 [Guide de réglage de performances SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 [Configuration de SQL Server pour les Services de R](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [R et optimisation des données](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)