---
title: Groupes de calcul dans les modèles tabulaires Analysis Services | Microsoft Docs
ms.date: 07/24/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: af63f41555a021fc720c7d1e15778265fe7de500
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419527"
---
# <a name="calculation-groups-preview"></a>Groupes de calcul (version préliminaire)
 
[!INCLUDE[ssas-appliesto-sql2019-aas](../../includes/ssas-appliesto-sql2019-aas.md)]

Les groupes de calcul peuvent réduire de manière significative le nombre de mesures redondantes en regroupant les expressions de mesure communes en tant qu' *éléments de calcul*. Les groupes de calcul sont pris en charge dans les modèles tabulaires Azure Analysis Services et SQL Server Analysis Services 2019 au [niveau de compatibilité](compatibility-level-for-tabular-models-in-analysis-services.md)1470 et supérieur. Les modèles au niveau de compatibilité 1470 sont actuellement en version **préliminaire**.  

Cet article aborde les points suivants : 

> [!div class="checklist"]
> * Avantages 
> * Fonctionnement des groupes de calcul
> * Chaînes de format dynamique
> * Commandé
> * Priorité
> * Outils
> * Limites



## <a name="benefits"></a>Avantages

Les groupes de calcul résolvent un problème dans les modèles complexes où il peut y avoir une prolifération de mesures redondantes utilisant les mêmes calculs (les plus courants avec les calculs Time-Intelligence). Par exemple, un analyste des ventes souhaite afficher les totaux des ventes et les commandes par mois à jour (MTD), trimestre à ce jour (Taj), année à jour (CÀJ), commandes année à jour pour l’année précédente (PY), et ainsi de suite. Le modeleur de données doit créer des mesures distinctes pour chaque calcul, ce qui peut entraîner des dizaines de mesures. Pour l’utilisateur, cela peut signifier qu’il faut trier le nombre de mesures et les appliquer individuellement à son rapport. 

Voyons tout d’abord comment les groupes de calcul apparaissent aux utilisateurs dans un outil de création de rapports comme Power BI. Nous examinerons ensuite ce qui constitue un groupe de calcul et comment ils sont créés dans un modèle.

Les groupes de calcul apparaissent dans les rapports de clients sous forme de table avec une seule colonne. La colonne n’est pas similaire à une colonne ou à une dimension standard, mais elle représente un ou plusieurs calculs réutilisables ou des *éléments de calcul* qui peuvent être appliqués à toute mesure déjà ajoutée au filtre valeurs pour une visualisation.

Dans l’animation suivante, un utilisateur analyse les données de ventes pour les années 2012 et 2013. Avant d’appliquer un groupe de calcul, la mesure de base commune **Sales** calcule la somme des ventes totales pour chaque mois. L’utilisateur souhaite ensuite appliquer des calculs Time Intelligence pour obtenir le total des ventes pour le mois jusqu’à la date, le trimestre jusqu’à la date, l’année jusqu’à ce jour, etc. Sans les groupes de calcul, l’utilisateur doit sélectionner des mesures d’intelligence temporelle individuelles.

Avec un groupe de calcul, dans cet exemple nommé **Time Intelligence**, lorsque l’utilisateur fait glisser l’élément de **calcul Time** vers la zone de filtre **colonnes** , chaque élément de calcul apparaît sous la forme d’une colonne distincte. Les valeurs de chaque ligne sont calculées à partir de la mesure de base **ventes**.  

![Groupe de calcul appliqué dans Power BI](media/calculation-groups/calc-groups-pbi.gif)


Les groupes de calcul  fonctionnent avec des mesures Dax explicites. Dans cet exemple, **Sales** est une mesure explicite déjà créée dans le modèle. Les groupes de calcul ne fonctionnent pas avec les mesures DAX implicites. Par exemple, dans Power BI les mesures implicites sont créées lorsqu’un utilisateur fait glisser des colonnes sur des éléments visuels pour afficher des valeurs agrégées, sans créer de mesure explicite. À ce stade, Power BI génère DAX pour les mesures implicites écrites en tant que calculs DAX Inline, ce qui signifie que les mesures implicites ne peuvent pas fonctionner avec les groupes de calcul. Une nouvelle propriété de modèle visible dans le modèle d’objet tabulaire (TOM) a été introduite, **DiscourageImplicitMeasures**. Actuellement, afin de créer des groupes de calcul, cette propriété doit avoir la valeur **true**. Quand la valeur est true, Power BI Desktop en mode Live Connect désactive la création de mesures implicites.

## <a name="how-they-work"></a>Fonctionnement

Maintenant que vous avez vu comment les groupes de calcul bénéficient des utilisateurs, jetons un coup d’œil sur la création de l’exemple de groupe de calcul Time Intelligence.

Avant d’aborder les détails, nous allons introduire de nouvelles fonctions DAX spécifiquement pour les groupes de calcul: 

[SELECTEDMEASURE](https://docs.microsoft.com/dax/selectedmeasure-function-dax) : utilisé par les expressions pour les éléments de calcul pour référencer la mesure actuellement en contexte. Dans cet exemple, la mesure Sales.

[SELECTEDMEASURENAME](https://docs.microsoft.com/dax/selectedmeasurename-function-dax) : utilisé par les expressions pour les éléments de calcul pour déterminer la mesure en contexte par nom.

[ISSELECTEDMEASURE](https://docs.microsoft.com/dax/isselectedmeasure-function-dax) : utilisé par les expressions pour les éléments de calcul pour déterminer la mesure en contexte est spécifiée dans une liste de mesures.

[SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasureformatstring-function-dax) : utilisé par les expressions pour les éléments de calcul pour récupérer la chaîne de format de la mesure en contexte.

### <a name="time-intelligence-example"></a>Exemple Time Intelligence

Nom de table- **intelligence temporelle**   
Nom de colonne- **calcul du temps**   
Précédence- **20**   

#### <a name="time-intelligence-calculation-items"></a>Éléments de calcul Time Intelligence

**Current**

```dax
SELECTEDMEASURE()
```

**MENSUELLE**

```dax
CALCULATE(SELECTEDMEASURE(), DATESMTD(DimDate[Date]))
```

**TRIMESTRE**

```dax
CALCULATE(SELECTEDMEASURE(), DATESQTD(DimDate[Date]))
```

**YTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

**EXERCICE**

```dax
CALCULATE(SELECTEDMEASURE(), SAMEPERIODLASTYEAR(DimDate[Date]))
```

**PY MTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "MTD"
)
```

**PY TAJ**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "QTD"
)
```

**PY AAD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

**YOY**

```dax
SELECTEDMEASURE() –
CALCULATE(
    SELECTEDMEASURE(),
    'Time Intelligence'[Time Calculation] = "PY"
)
```

**YOY**

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

Pour tester ce groupe de calcul, vous pouvez exécuter une requête DAX dans SSMS ou dans le Open source [Dax Studio](http://daxstudio.org/). YOY et YOY% sont omis de cet exemple de requête.

#### <a name="time-intelligence-query"></a>Requête Time Intelligence

```dax
EVALUATE
CALCULATETABLE (
    SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Current", CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "Current" ),
        "QTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "QTD" ),
        "YTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "YTD" ),
        "PY",      CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY" ),
        "PY QTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY QTD" ),
        "PY YTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY YTD" )
    ),
    DimDate[CalendarYear] IN { 2012, 2013 }
)
```

#### <a name="time-intelligence-query-return"></a>Retour de requête Time Intelligence

La table de retour indique les calculs pour chaque élément de calcul appliqué. Par exemple, vous pouvez voir Taj pour le 2012 mars est la somme du 1er janvier, du février et du 2012 mars.

![Requête de retour](media/calculation-groups/calc-groups-query-return.png)


## <a name="dynamic-format-strings"></a>Chaînes de format dynamique

Les *chaînes de format dynamique* avec des groupes de calcul permettent l’application conditionnelle de chaînes de format à des mesures sans les forcer à retourner des chaînes.

Les modèles tabulaires prennent en charge la mise en forme dynamique des mesures à l’aide de la fonction [format](https://docs.microsoft.com/dax/format-function-dax) de Dax. Toutefois, la fonction FORMAT présente l’inconvénient de retourner une chaîne, en forçant les mesures qui, autrement, seraient numériques à être retournées sous forme de chaîne. Cela peut avoir des limitations, telles que le non-fonctionnement de la plupart des éléments visuels Power BIen fonction des valeurs numériques, comme les graphiques.

### <a name="dynamic-format-strings-for-time-intelligence"></a>Chaînes de format dynamiques pour Time Intelligence

Si nous examinons l’exemple Time Intelligence indiqué ci-dessus, tous les éléments de calcul, à l’exception de **YOY%** , doivent utiliser le format de la mesure actuelle en contexte. Par exemple, **AAJ** calculé sur la mesure Sales base doit être Currency. S’il s’agit d’un groupe de calcul pour un résultat comme une mesure de base Orders, le format serait numeric. **YOY%** , toutefois, doit être un pourcentage, quel que soit le format de la mesure de base.

Pour **YOY%** , nous pouvons remplacer la chaîne de format en affectant à la propriété expression de chaîne de format la valeur **0,00%;-0,00%; 0,00%** . Pour en savoir plus sur les propriétés de l’expression de chaîne de format, consultez [Propriétés de la cellule MDX-format du contenu de la chaîne](../multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md#numeric-values).

Dans ce visuel de matrice dans Power BI, vous voyez **ventes Current/YOY** et **Orders Current/YOY** conserver leurs chaînes de format de mesure de base respectives. Les **ventes YOY%** et les **commandes YOY%** , toutefois, remplacent la chaîne de format pour utiliser le format de *pourcentage* .

![Time Intelligence dans le visuel de matrice](media/calculation-groups/calc-groups-dynamicstring-timeintel.png)

### <a name="dynamic-format-strings-for-currency-conversion"></a>Chaînes de format dynamique pour la conversion monétaire

Les chaînes de format dynamiques fournissent une conversion de devise simple. Considérons le modèle de données Adventure Works suivant. Elle est modélisée pour *une conversion monétaire un-à-plusieurs* , comme défini par les [types de conversion](../currency-conversions-analysis-services.md#conversion-types).

![Taux monétaire dans le modèle tabulaire](media/calculation-groups/calc-groups-currency-conversion.png)

Une colonne **FormatString** est ajoutée à la table **DimCurrency** et remplie avec des chaînes de format pour les devises respectives.

![Colonne de chaîne de format](media/calculation-groups/calc-groups-formatstringcolumn.png)

Pour cet exemple, le groupe de calcul suivant est ensuite défini comme suit:

### <a name="currency-conversion-example"></a>Exemple de conversion monétaire

Nom de la table- **conversion monétaire**   
Nom de colonne- **calcul de conversion**   
Précédence- **5**   

#### <a name="calculation-items-for-currency-conversion"></a>Éléments de calcul pour la conversion monétaire

**Aucune conversion**

```dax
SELECTEDMEASURE()
```

**Devise convertie**

```dax
IF(
    //Check one currency in context & not US Dollar, which is the pivot currency:
    SELECTEDVALUE( DimCurrency[CurrencyName], "US Dollar" ) = "US Dollar",
    SELECTEDMEASURE(),
    SUMX(
        VALUES(DimDate[Date]),
        CALCULATE( DIVIDE( SELECTEDMEASURE(), MAX(FactCurrencyRate[EndOfDayRate]) ) )
    )
)
```

Expression de chaîne de format

```dax
SELECTEDVALUE(
    DimCurrency[FormatString],
    SELECTEDMEASUREFORMATSTRING()
)
```
L’expression de chaîne de format doit retourner une chaîne scalaire. Elle utilise la nouvelle fonction [SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasureformatstring-function-dax) pour revenir à la chaîne de format de mesure de base s’il existe plusieurs devises dans le contexte de filtre.

L’animation suivante montre la conversion de devises au format dynamique de la mesure **Sales** dans un rapport.

![Chaîne de format dynamique de conversion monétaire appliquée](media/calculation-groups/calc-groups-dynamic-format-string.gif)

## <a name="precedence"></a>Priorité

La priorité est une propriété définie pour un groupe de calcul. Elle spécifie l’ordre d’évaluation lorsqu’il existe plusieurs groupes de calcul. Un nombre plus élevé indique une priorité plus élevée, ce qui signifie qu’il sera évalué avant les groupes de calcul avec une priorité plus faible.

Pour cet exemple, nous allons utiliser le même modèle que l’exemple Time-Intelligence ci-dessus, mais  également ajouter un groupe de calcul Averages. Le groupe de calcul Averages contient des calculs moyens qui sont indépendants de l’intelligence temporelle traditionnelle en ce sens qu’ils ne changent pas le contexte de filtre de date: ils appliquent simplement des calculs moyens.

Dans cet exemple, un calcul de moyenne quotidienne est défini. Les calculs tels que les barils moyens d’huile par jour sont courants dans les applications de pétrole et de gaz. Parmi les autres exemples courants, citons la moyenne des ventes de magasins dans la vente au détail.

Bien que ces calculs soient calculés indépendamment des calculs Time-Intelligence, il peut être nécessaire de les combiner. Par exemple, un utilisateur peut souhaiter voir les barils de pétrole par jour AAD pour afficher le taux d’huile quotidien entre le début de l’année et la date actuelle. Dans ce scénario, la priorité doit être définie pour les éléments de calcul.

### <a name="averages-example"></a>Exemple de moyennes

Le nom de la table est Averages.   
Le nom de la colonne est **calcul moyen**.   
La précédence est de **10**.   

#### <a name="calculation-items-for-averages"></a>Éléments de calcul pour les moyennes

**Aucune moyenne**

```dax
SELECTEDMEASURE()
```

**Moyenne quotidienne**

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Voici un exemple de requête DAX et de table de retour:

#### <a name="averages-query"></a>Moyenne des requêtes

```dax
EVALUATE
    CALCULATETABLE (
        SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Sales", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "No Average"
        ),
        "YTD", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "No Average"
        ),
        "Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "Daily Average"
        ),
        "YTD Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "Daily Average"
        )
    ),
    DimDate[CalendarYear] = 2012
)
```

#### <a name="averages-query-return"></a>Nombre moyen de requêtes de retour

![Requête de retour](media/calculation-groups/calc-groups-ytd-daily-avg.png)

Le tableau suivant montre comment les valeurs de mars 2012 sont calculées.


|Nom de la colonne  |Calcul |
|---------|---------|
|YTD     |    Somme des ventes pour Jan, fév, Mar 2012<br />= 495 364 + 506 994 + 373 483     |
|Moyenne quotidienne    |     Ventes pour le Mar 2012 divisé par le nombre de jours en mars<br />= 373 483/31       |
|Moyenne quotidienne AAD     | CÀJ pour le Mar 2012 divisé par nombre de jours en Jan, fév et Mar<br />= 1 375 841/(31 + 29 + 31)       |

Voici la définition de l’élément de calcul AAJ, appliquée avec la précédence **20**.

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

Voici la moyenne quotidienne appliquée avec une précédence de **10**.

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Étant donné que la priorité du groupe de calcul Time Intelligence est supérieure à celle du groupe de calcul Averages, il est appliqué aussi largement que possible. Le calcul annuel moyen quotidien s’applique au numérateur et au dénominateur (nombre de jours) du calcul de la moyenne quotidienne.

Cela équivaut à l’expression suivante:

```dax
CALCULATE(DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate)), DATESYTD(DimDate[Date]))
```

Cette expression n’est pas:

```dax
DIVIDE(CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date])), COUNTROWS(DimDate)))
```

## <a name="sideways-recursion"></a>Récursivité latérale

Dans l’exemple Time Intelligence ci-dessus, certains éléments de calcul font référence à d’autres dans le même groupe de calcul. C’est ce que l’on appelle la *récursivité latérale*. Par exemple, **YOY%** fait référence à la fois à **YOY** et à **py**.

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

Dans ce cas, les deux expressions sont évaluées séparément, car elles utilisent des instructions Calculate différentes. Les autres types de récurrence ne sont pas pris en charge.

## <a name="single-calculation-item-in-filter-context"></a>Élément de calcul unique dans le contexte de filtre

Dans notre exemple Time Intelligence, l’élément de calcul **py AAD** a une expression Calculate unique:

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

L’argument AAJ de la fonction CALCULATE () remplace le contexte de filtre pour réutiliser la logique déjà définie dans l’élément de calcul AAJ. Il n’est pas possible d’appliquer à la fois PY et AAD en une seule évaluation. Les groupes de calcul sont *appliqués uniquement* si un seul élément de calcul du groupe de calcul se trouve dans le contexte de filtre.

## <a name="mdx-support"></a>Prise en charge MDX

Les groupes de calcul prennent en charge les requêtes MDX (Multidimensional Data expressions). Cela signifie que les utilisateurs de Microsoft Excel, qui interrogent des modèles de données tabulaires à l’aide de MDX, peuvent tirer pleinement parti des groupes de calcul dans les tableaux croisés dynamiques et les graphiques de feuille de calcul.

## <a name="tools"></a>Outils

Les groupes de calcul ne sont pas encore pris en charge dans SQL Server Data Tools, Visual Studio avec les extensions Analysis Services. Toutefois, vous pouvez créer des groupes de calcul à l’aide du langage TMSL (Tabular Model Scripting Language) ou de l' [éditeur tabulaire](https://github.com/otykier/TabularEditor)Open source.

## <a name="limitations"></a>Limites

[Sécurité au niveau](object-level-security.md) de l’objet (OLS) défini sur les tables de groupes de calcul n’est pas pris en charge. Toutefois, OLS peut être défini sur d’autres tables dans le même modèle. Si un élément de calcul fait référence à un objet sécurisé OLS, une erreur générique est retournée.

[Sécurité au niveau des lignes](roles-ssas-tabular.md#bkmk_rowfliters) (RLS) n’est pas pris en charge. Vous pouvez définir la sécurité au niveau des lignes sur des tables dans le même modèle, mais pas sur des groupes de calcul eux-mêmes (directement ou indirectement).

## <a name="see-also"></a>Voir aussi  

[DAX dans les modèles tabulaires](understanding-dax-in-tabular-models-ssas-tabular.md)   
[Référence DAX](https://docs.microsoft.com/dax/data-analysis-expressions-dax-reference)  
