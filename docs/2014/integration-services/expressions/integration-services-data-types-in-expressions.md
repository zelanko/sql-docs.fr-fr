---
title: Types de données Integration Services dans les expressions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], data types
- data types [Integration Services], expressions
ms.assetid: c296ad10-4080-4988-8c2c-2c250f7a1884
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3283810af4de66a43820c865bdd7c41aaa1657ec
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428576"
---
# <a name="integration-services-data-types-in-expressions"></a>Types de données Integration Services dans les expressions
  L'évaluateur d'expression utilise des types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Lorsque des données entrent dans un flux de données d'un package [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , le moteur de flux de données convertit toutes les données de colonne vers un type de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] et les données de colonne utilisées par une expression ont déjà un type de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Les expressions utilisées dans les transformations de fractionnement conditionnel et de colonne dérivée peuvent référencer des colonnes car elles font partie d'un flux de données qui comprend des données de colonne.

## <a name="variables"></a>Variables
 Les expressions peuvent également utiliser des variables. Les variables ont un type de données Variant et l'évaluateur d'expression convertit le type de données d'une variable d'un sous-type Variant vers un type de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] avant d'évaluer l'expression. Les variables ne peuvent utiliser qu'un sous-ensemble des types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Par exemple, une variable ne peut pas utiliser un type de données BLOB (Binary Large Object Block).

 Pour plus d’informations sur les types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] et le mappage des types de données Variant à des types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , consultez [Types de données d’Integration Services](../data-flow/integration-services-data-types.md).

## <a name="literals"></a>Littéraux
 Les expressions peuvent aussi comprendre des littéraux de chaîne, booléens et numériques. Pour plus d’informations sur la conversion des littéraux numériques vers des types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] numériques, consultez [Littéraux &#40;SSIS&#41;](numeric-string-and-boolean-literals.md).

## <a name="implicit-data-conversion"></a>Conversion de données implicite
 Une conversion implicite d'un type de données se produit lorsque l'évaluateur d'expression convertit automatiquement les données d'un type de données vers un autre. Par exemple, si un `smallint` est comparé à un `int`, le `smallint` est implicitement converti en `int` avant que la comparaison soit réalisée.

 L'évaluateur d'expression ne peut pas effectuer la conversion implicite des données lorsque les arguments et les opérandes contiennent des types de données incompatibles. Par ailleurs, l'évaluateur d'expression ne peut pas convertir implicitement une valeur en une valeur booléenne. Les arguments et les opérandes doivent être donc être converties explicitement en utilisant l'opérateur de cast. Pour plus d’informations, consultez [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).

 Le diagramme suivant indique le type de résultat des conversions implicites des opérations BINARY. L'intersection d'une colonne et d'une ligne produit le même type de résultat d'une opération binaire avec des opérandes des types gauche (From) et droit (To).

 ![Conversion de type de données implicite entre types de données](../media/mw-dts-impl-conver-02.gif "Conversion de type de données implicite entre types de données")

 L'intersection d'un entier signé et d'un entier non signé est un entier signé potentiellement plus grand que l'un ou l'autre des arguments.

 Les opérateurs comparent des chaînes, des dates, des valeurs booléennes et d'autres types de données. Avant qu'un opérateur ne compare deux valeurs, l'évaluateur d'expression effectue certaines conversions implicites. L'évaluateur d'expression convertit toujours les littéraux de chaîne vers le type de données DT_WSTR et les littéraux booléens vers le type de données DT_BOOL. L'évaluateur d'expression interprète toutes les valeurs entre guillemets comme des chaînes. Les littéraux numériques sont convertis vers l'un des types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] numériques.

> [!NOTE]
>  Les valeurs booléennes ne sont pas des nombres mais des valeurs logiques. Bien que les valeurs booléennes peuvent apparaître sous la forme de nombres dans certains environnements, elles ne sont pas stockées en tant que tels et divers langages de programmation les représentent de manière différente en tant que valeurs numériques, notamment les méthodes .NET Framework.
> 
>  Par exemple, les fonctions de conversion disponibles dans Visual Basic convertissent la valeur `True` en -1 ; toutefois, la méthode `System.Convert.ToInt32` du .NET Framework convertit `True` en +1. Le langage d'expression [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] convertit `True` en -1.
> 
>  Pour éviter des erreurs ou des résultats inattendus, n'écrivez pas de code fondé sur des valeurs numériques précises pour les valeurs `True` et `False`. Si possible, limitez l'utilisation de variables booléennes aux valeurs logiques pour lesquelles elles sont conçues.

 Pour plus d'informations, voir les rubriques suivantes :

-   [== &#40;Égal&#41; &#40;expression SSIS&#41;](equal-ssis-expression.md)

-   [! = &#40;&#41; &#40;Expression SSIS inégale&#41;](unequal-ssis-expression.md)

-   [&#62; &#40;Supérieur à&#41; &#40;expression SSIS&#41;](greater-than-ssis-expression.md)

-   [&#60; &#40;Inférieur à&#41; &#40;expression SSIS&#41;](less-than-ssis-expression.md)

-   [&#62;= &#40;Supérieur ou égal à&#41; &#40;expression SSIS&#41;](greater-than-or-equal-to-ssis-expression.md)

-   [&#60;= &#40;Inférieur ou égal à&#41; &#40;expression SSIS&#41;](less-than-or-equal-to-ssis-expression.md)

 Une fonction qui utilise un seul argument retourne un résultat dont le type de données est celui de l'argument, sauf dans les cas suivants :

-   Les fonctions DAY, MONTH et YEAR acceptent une date et renvoient un résultat entier (DT_I4).

-   La fonction ISNULL accepte une expression de n’importe quel type de données [!INCLUDE[ssIS](../../includes/ssis-md.md)] et retourne un résultat booléen (DT_BOOL).

-   Les fonctions SQUARE et SQRT acceptent une expression numérique et renvoient un résultat numérique non intégral (DT_BOOL).

 Si les arguments possèdent le même type de données, le résultat est de ce type. La seule exception est une opération binaire sur deux valeurs de type de données DT_DECIMAL, car celle-ci retourne un résultat dont le type de données est DT_NUMERIC.

## <a name="requirements-for-data-used-in-expressions"></a>Configuration requise pour les données utilisées dans les expressions
 L'évaluateur d'expression prend en charge tous les types de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Toutefois, selon l'opération ou la fonction, les opérandes et les arguments requièrent certains types de données. L'évaluateur d'expression impose les contraintes suivantes en matière de type de données pour les données utilisées dans les expressions :

-   Les opérandes utilisés dans les opérations **logiques** doivent s'évaluer à une valeur booléenne. Par exemple, ColonneA > 1&&ColonneB < 2.

-   Les opérandes utilisés dans les opérations **mathématiques** doivent s'évaluer à une valeur numérique. Par exemple, 23,75 * 4.

-   Les opérandes utilisés dans les opérations de comparaison, telles que les opérations logiques et d'égalité, doivent correspondre à des types de données compatibles.

     Par exemple, l'une des expressions de l'exemple suivant utilise le type de données DT_DBTIMESTAMPOFFSET :

     `(DT_DBTIMESTAMPOFFSET,3) "1999-10-11 20:34:52.123 -3:30" != (DT_DBDATE)"1999-10-12"`

     Le système convertit l’expression `(DT_DBDATE)"1999-10-12"`en DT_DBTIMESTAMPOFFSET. Cet exemple correspond à TRUE car l'expression convertie devient "1999-10-12 00:00:00.000 +00:00", ce qui n'est pas égal à la valeur de l'autre expression, `(DT_DBTIMESTAMPOFFSET,3) "1999-10-11 20:34:52.123 -3:30"`.

-   Les arguments transmis aux fonctions mathématiques doivent s'évaluer à un type de données numérique. Selon la fonction ou l'opération, un type de données numérique spécifique peut être requis. Par exemple, la fonction HEX requiert un entier signé ou non signé.

-   Les arguments passés aux fonctions de chaîne doivent produire un type de données caractère : DT_STR ou DT_WSTR. Par exemple, UPPER("fleur"). Certaines fonctions de chaîne, telles que la fonction SUBSTRING, requièrent des arguments entiers supplémentaires pour définir la position de début et la longueur de la chaîne.

-   Les arguments transmis aux fonctions de date et d'heure doivent s'évaluer à une date valide. Par exemple, DAY(GETDATE()). Certaines fonctions, telles que la fonction DATEADD, requièrent un argument entier supplémentaire pour définir le nombre de jours qu'elles ajoutent à une date.

 Les opérations qui combinent un entier non signé (8 bits) et un entier signé nécessitent une conversion explicite afin de clarifier le format du résultat. Pour plus d’informations, consultez [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).

 Les résultats de nombreuses opérations et fonctions ont des types de données prédéterminés. Il peut s'agir du type de données de l'argument ou du type de données vers lequel l'évaluateur d'expression convertit le résultat. Par exemple, le résultat d'un opérateur logique OU (||) est toujours booléen, le résultat de la fonction ABS a le type de données numérique de l'argument et le résultat de la multiplication est du plus petit type de données numérique pouvant contenir ce résultat sans perte de données. Pour plus d’informations sur les types de données des résultats, consultez [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md) et [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md).

## <a name="related-tasks"></a>Tâches associées
 [Utiliser une expression dans un composant de flux de données](../use-an-expression-in-a-data-flow-component.md)

## <a name="related-content"></a>Contenu associé

-   Article technique, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet3), sur pragmaticworks.com

-   Article technique, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), sur social.technet.microsoft.com


