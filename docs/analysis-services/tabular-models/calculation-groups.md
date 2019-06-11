---
title: Les groupes de calcul dans les modèles tabulaires Analysis Services | Microsoft Docs
ms.date: 06/09/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: abc1f51d21613676fd94271f931e1a7692cc1efc
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822694"
---
# <a name="calculation-groups-preview"></a>Groupes de calcul (version préliminaire)
 
[!INCLUDE[ssas-appliesto-sql2019-aas](../../includes/ssas-appliesto-sql2019-aas.md)]

Groupes de calcul peuvent réduire considérablement le nombre de mesures redondants en regroupant les expressions de mesures courantes en tant que *des éléments de calcul*. Groupes de calcul sont pris en charge dans Azure Analysis Services et SQL Server Analysis Services 2019 tabulaires des modèles à partir de la 1470 [niveau de compatibilité](compatibility-level-for-tabular-models-in-analysis-services.md). Modèles au niveau de compatibilité 1470 sont actuellement en **aperçu**.  

Cet article décrit : 

> [!div class="checklist"]
> * Avantages 
> * Comment fonctionnent les groupes de calcul
> * Chaînes de format dynamique
> * Priorité
> * Outils
> * Limitations



## <a name="benefits"></a>Avantages

Groupes de calcul de résoudre un problème dans les modèles complexes où il peut y avoir une prolifération des mesures redondants à l’aide des mêmes calculs - courants avec des calculs time intelligence. Par exemple, un analyste des ventes souhaite afficher des totaux des ventes trie par mois-to-date (MTD), quarter-to-date (QTD), year-to-date (YTD), les commandes year-to-date pour l’année précédente (PY) et ainsi de suite. Le Modélisateur de données doit créer des mesures distinctes pour chaque calcul, ce qui peut entraîner des dizaines de mesures. Pour l’utilisateur, cela peut signifier que rencontre à trier simplement autant de mesures et les appliquer individuellement à leur rapport. 

Nous allons tout d’abord Examinons comment les groupes de calcul s’affichent aux utilisateurs dans un outil de création de rapports comme Power BI. Nous allons ensuite examiner en quoi consiste un groupe de calcul, et comment elles sont créées dans un modèle.

Les groupes de calcul apparaissent dans les rapports de clients sous forme de table avec une seule colonne. La colonne n’est pas comme une colonne classique ou d’une dimension, au lieu de cela, il représente un ou plusieurs calculs réutilisables, ou *des éléments de calcul* qui peut être appliqué à toute mesure déjà ajouté au filtre de valeurs pour une visualisation.

Dans l’animation suivante, un utilisateur analyse les données de ventes pour les années 2012 et 2013. Avant d’appliquer un groupe de calcul, la mesure de base commun **ventes** calcule une somme du total des ventes pour chaque mois. Ensuite, l’utilisateur souhaite appliquer des calculs time intelligence pour obtenir les ventes totales pour le mois jusqu'à ce jour, trimestre à ce jour, année jusqu'à ce jour et ainsi de suite. Sans les groupes de calcul, l’utilisateur a sélectionner les mesures individuelles time intelligence.

Avec un groupe de calcul, dans cet exemple nommé **Time Intelligence**, lorsque l’utilisateur fait glisser le **calcul du temps** d’élément à la **colonnes** zone, chaque élément de calcul de filtre apparaît sous la forme d’une colonne distincte. Valeurs pour chaque ligne sont calculées à partir de la mesure de base, **Sales**.  

![Groupe de calcul appliquée dans Power BI](media/calculation-groups/calc-groups-pbi.gif)


Groupes de calcul fonctionnent avec **explicite** mesures DAX. Dans cet exemple, **Sales** est une mesure explicite déjà créée dans le modèle. Groupes de calcul ne fonctionnent pas avec les mesures DAX implicites. Par exemple, dans Power BI les mesures implicites sont créés quand un utilisateur fait glisser des colonnes sur les éléments visuels pour afficher des valeurs agrégées, sans créer une mesure explicite. À ce stade, Power BI génère DAX des mesures implicites écrits, sous la forme inline, les calculs DAX - ce qui signifie que les mesures implicites ne fonctionnent pas avec les groupes de calcul. Une nouvelle propriété de modèle visible dans le modèle d’objet tabulaire (TOM) a été introduite, **DiscourageImplicitMeasures**. Actuellement, afin de créer des groupes de calcul de cette propriété doit être définie sur **true**. Lorsque la valeur est true, Power BI Desktop dans Live Connect mode désactive la création de mesures implicites.

## <a name="how-they-work"></a>Leur fonctionnement

Maintenant que vous avez vu comment les utilisateurs de bénéficier de groupes de calcul, jetons un œil à la création de l’exemple de groupe de calcul de Time Intelligence indiqué.

Avant de rentrer dans les détails, nous allons présenter certaines nouvelles fonctions DAX en particulier pour les groupes de calcul : 

[SELECTEDMEASURE](https://docs.microsoft.com/dax/selectedmeasure-function-dax) - utilisés par des expressions pour les éléments de calcul référencer la mesure est actuellement dans le contexte. Dans cet exemple, la mesure Sales.

[SELECTEDMEASURENAME](https://docs.microsoft.com/dax/selectedmeasurename-function-dax) - utilisés par des expressions pour les éléments de calcul déterminer la mesure qui se trouve dans le contexte par nom.

[ISSELECTEDMEASURE](https://docs.microsoft.com/dax/isselectedmeasure-function-dax) - utilisés par des expressions pour les éléments de calcul déterminer la mesure qui se trouve dans le contexte est spécifiée dans une liste de mesures.

[SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax) - utilisés par des expressions pour les éléments de calcul récupérer la chaîne de format de la mesure qui se trouve dans le contexte.

### <a name="time-intelligence-example"></a>Exemple d’analyse décisionnelle de temps

Nom de la table - **Time Intelligence**   
Nom de colonne - **calcul du temps**   
Priorité - **20**   

#### <a name="time-intelligence-calculation-items"></a>Éléments de calcul d’Intelligence temps

**Current**

```dax
SELECTEDMEASURE()
```

**MTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESMTD(DimDate[Date]))
```

**QTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESQTD(DimDate[Date]))
```

**YTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

**PY**

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

**PY QTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "QTD"
)
```

**PY YTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

**CHAQUE ANNÉE**

```dax
SELECTEDMEASURE() –
CALCULATE(
    SELECTEDMEASURE(),
    'Time Intelligence'[Time Calculation] = "PY"
)
```

**YOY%**

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

Pour tester ce groupe de calcul, vous pouvez exécuter une requête DAX dans SSMS ou open source [DAX Studio](http://daxstudio.org/). YOY et YOY % sont omis de cet exemple de requête.

#### <a name="time-intelligence-query"></a>Requête de Time Intelligence

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

#### <a name="time-intelligence-query-return"></a>Retour de la requête de Time Intelligence

La table de retour montre des calculs pour chaque calcul élément appliqué. Par exemple, vous pouvez voir que Qtd pour mars 2012 est la somme de janvier, février et mars 2012.

![Retour de la requête](media/calculation-groups/calc-groups-query-return.png)


## <a name="dynamic-format-strings"></a>Chaînes de format dynamique

*Chaînes de format dynamique* avec calcul groupes permettent à une application conditionnelle de chaînes de format de mesures sans les forcer à retourner des chaînes.

Les modèles tabulaires prennent en charge la mise en forme dynamique des mesures à l’aide de DAX [FORMAT](https://docs.microsoft.com/dax/format-function-dax) (fonction). Toutefois, la fonction FORMAT présente l’inconvénient de retourner une chaîne, en forçant les mesures qui seraient autrement numériques doit également être retournée sous forme de chaîne. Cela peut avoir certaines limitations, telles que ne fonctionne ne pas avec la plupart des éléments visuels Power BI en fonction des valeurs numériques, tels que des graphiques.

### <a name="dynamic-format-strings-for-time-intelligence"></a>Chaînes de format dynamique pour time intelligence

Si nous examinons l’exemple Time Intelligence ci-dessus, le calcul de tous les éléments sauf **YOY %** doit utiliser le format de la mesure actuelle dans le contexte. Par exemple, **YTD** calculé sur la mesure de base de ventes doit être de devise. S’il s’agissait d’un groupe de calcul pour quelque chose comme une mesure de base de commandes, le format serait numérique. **Variation en pourcentage**, toutefois, doit être un pourcentage, quel que soit le format de la mesure de base.

Pour **YOY %** , nous pouvons remplacer la chaîne de format en définissant la propriété expression de chaîne de format **0,00 % ;-0.00 ; 0,00 %** . Pour en savoir plus sur les propriétés d’expression de chaîne de format, consultez [propriétés de cellule MDX - contenu de chaîne de FORMAT](../multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md#numeric-values).

Dans cette matrice visuel dans Power BI, vous voyez **Sales actuel/YOY** et **Orders actuel/YOY** conserver leurs chaînes de format de mesure de base respectifs. **Variation en pourcentage ventes** et **variation en pourcentage des commandes**, toutefois, remplace la chaîne de format à utiliser *pourcentage* format.

![Fonctions Time intelligence dans le visuel de matrice](media/calculation-groups/calc-groups-dynamicstring-timeintel.png)

### <a name="dynamic-format-strings-for-currency-conversion"></a>Chaînes de format dynamique pour la conversion monétaire

Chaînes de format dynamique fournissent la conversion monétaire facile. Considérez le modèle de données Adventure Works suivant. Elle est modélisée pour *un-à-plusieurs* tel que défini par la conversion monétaire [types de Conversion](../currency-conversions-analysis-services.md#conversion-types).

![Taux de devise dans le modèle tabulaire](media/calculation-groups/calc-groups-currency-conversion.png)

Un **FormatString** colonne est ajoutée à la **DimCurrency** table et rempli avec les chaînes de format pour les devises respectifs.

![Colonne de chaîne de format](media/calculation-groups/calc-groups-formatstringcolumn.png)

Pour cet exemple, le groupe de calcul suivant est alors défini en tant que :

### <a name="currency-conversion-example"></a>Exemple de Conversion de devise

Nom de la table - **Conversion monétaire**   
Nom de colonne - **calcul de Conversion**   
Priorité - **5**   

#### <a name="calculation-items-for-currency-conversion"></a>Éléments de calcul pour la Conversion de devise

**Aucune Conversion**

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
L’expression de chaîne de format doit renvoyer une chaîne scalaire. Il utilise le nouveau [SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax) (fonction) pour rétablir la chaîne de format de mesure de base s’il existe plusieurs devises dans le contexte de filtre.

L’animation suivante montre la conversion de devise format dynamique de la **Sales** mesure dans un rapport.

![Chaîne de format dynamique de conversion monétaire appliqué](media/calculation-groups/calc-groups-dynamic-format-string.gif)

## <a name="precedence"></a>Priorité

Priorité est une propriété définie pour un groupe de calcul. Il spécifie l’ordre d’évaluation lorsqu’il existe plus d’un groupe de calcul. Une valeur supérieure indique une priorité supérieure, ce qui signifie qu’il sera évaluée avant les groupes de calcul avec une priorité inférieure.

Pour cet exemple, nous allons utiliser le même modèle que l’exemple time intelligence ci-dessus, mais également ajouter un **moyennes** groupe de calcul. Le groupe de calcul de moyennes contient des calculs de moyenne qui sont indépendantes de l’intelligence temporelle traditionnel dans la mesure où ils ne changent pas le contexte de filtre de date : ils simplement appliquent des calculs de moyenne qu’il contient.

Dans cet exemple, un calcul de la moyenne quotidiens est défini. Calculs tels que barils moyenne d’huile par jour sont courantes dans les applications de pétrole et gaz. Autres exemples d’entreprise courantes incluent la moyenne des ventes magasin dans la vente au détail.

Bien que ces calculs sont calculées indépendamment les calculs time intelligence, il pourrait bien être obligé de les combiner. Par exemple, un utilisateur peut souhaiter voir barils d’huile par jour YTD pour afficher le taux de pétrole quotidien à partir du début de l’année la date actuelle. Dans ce scénario, la priorité doit être définie pour les éléments de calcul.

### <a name="averages-example"></a>Exemple de moyennes

Nom de la table est **moyennes**.   
Nom de colonne est **calcul moyen**.   
La priorité est **10**.   

#### <a name="calculation-items-for-averages"></a>Éléments de calcul de moyennes

**Aucune moyenne**

```dax
SELECTEDMEASURE()
```

**Moyenne quotidienne**

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Voici un exemple d’une requête DAX et la table de retour :

#### <a name="averages-query"></a>Requête de moyennes

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

#### <a name="averages-query-return"></a>Requête de moyennes retour

![Retour de la requête](media/calculation-groups/calc-groups-ytd-daily-avg.png)

Le tableau suivant indique comment les valeurs de mars 2012 sont calculés.


|Nom de colonne  |Calcul |
|---------|---------|
|YTD     |    Somme des ventes pour janvier, février, mars 2012<br />= 495,364 + 506,994 + 373,483     |
|Moyenne quotidienne    |     Ventes pour mars 2012 divisé par nombre de jours en mars<br />= 373,483 / 31       |
|Moyenne quotidienne YTD     | YTD pour mars 2012 divisé par nombre de jours de janvier, février et mars<br />=  1,375,841 / (31 + 29 + 31)       |

Voici la définition de l’élément de calcul YTD appliquée avec la priorité des **20**.

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

Voici quotidienne moyenne, appliquée avec une priorité de **10**.

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Étant donné que la priorité du groupe de calcul de Time Intelligence est supérieure à celui du groupe de calcul de moyennes, il est appliqué en tant qu’autant que possible. Le calcul YTD quotidienne moyenne s’applique à AAD pour le numérateur et dénominateur (nombre de jours) du calcul de moyenne quotidiens.

Cela équivaut à l’expression suivante :

```dax
CALCULATE(DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate)), DATESYTD(DimDate[Date]))
```

Pas de cette expression :

```dax
DIVIDE(CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date])), COUNTROWS(DimDate)))
```

## <a name="sideways-recursion"></a>Récursivité sur le côté

Dans l’exemple Time Intelligence ci-dessus, certains des éléments de calcul font référence à d’autres personnes dans le même groupe de calcul. Il s’agit *couchée recursion*. Par exemple, **YOY %** fait référence à la fois **YOY** et **PY**.

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

Dans ce cas, les deux expressions sont évaluées séparément, car ils sont à l’aide de différents calculer les instructions. Autres types de récursivité ne sont pas pris en charge.

## <a name="single-calculation-item-in-filter-context"></a>Élément de calcul unique dans le contexte de filtre

Dans notre exemple Time Intelligence, la **PY YTD** élément de calcul a une seule expression de calcul :

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

L’argument de l’année en cours à la fonction CALCULATE() remplace le contexte de filtre pour réutiliser la logique déjà définie dans l’élément de calcul YTD. Il n’est pas possible d’appliquer PY et YTD dans une évaluation unique. Groupes de calcul sont *uniquement appliqué* si un élément de calcul unique à partir du groupe de calcul se trouve dans le contexte de filtre.

## <a name="mdx-support"></a>Prise en charge MDX

Groupes de calcul prend en charge les requêtes de données multidimensionnelles (MDX). Cela signifie que, les utilisateurs de Microsoft Excel, les modèles de données tabulaires de requête à l’aide de MDX, peuvent tirer pleinement parti des groupes de calcul dans la feuille de calcul tableaux croisés dynamiques et graphiques.

## <a name="tools"></a>Outils

Groupes de calcul ne sont pas encore pris en charge dans SQL Server Data Tools, Visual Studio avec des extensions d’Analysis Services. Toutefois, les groupes de calcul peuvent être créés à l’aide de modèle tabulaire Scripting Language (TMSL) ou open source [éditeur tabulaire](https://github.com/otykier/TabularEditor).

## <a name="limitations"></a>Limitations

[Sécurité au niveau de l’objet](object-level-security.md) (OLS) défini sur le calcul des tables de groupe n’est pas pris en charge. Toutefois, OLS peuvent être définies sur les autres tables dans le même modèle. Si un élément de calcul fait référence à un objet sécurisé OLS, une erreur générique est retournée.

[Sécurité au niveau des lignes](roles-ssas-tabular.md#bkmk_rowfliters) (RLS) n’est pas pris en charge. Vous pouvez définir des lignes sur les tables dans le même modèle, mais pas sur les groupes de calcul eux-mêmes (directement ou indirectement).

[Décrit en détail les Expressions de lignes](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md) ne sont pas pris en charge avec les groupes de calcul.

## <a name="see-also"></a>Voir aussi  

[DAX dans les modèles tabulaires](understanding-dax-in-tabular-models-ssas-tabular.md)   
[Référence DAX](https://docs.microsoft.com/dax/data-analysis-expressions-dax-reference)  
