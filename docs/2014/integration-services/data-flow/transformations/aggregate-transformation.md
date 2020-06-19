---
title: Agrégation, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregatetrans.f1
helpviewer_keywords:
- IsBig property
- aggregate functions [Integration Services]
- Aggregate transformation [Integration Services]
- large data, SSIS transformations
ms.assetid: 2871cf2a-fbd3-41ba-807d-26ffff960e81
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8f97259e9388575c8a300ad6e4d1284e55443a60
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84913946"
---
# <a name="aggregate-transformation"></a>Transformation d'agrégation
  La transformation d’agrégation applique des fonctions d’agrégation, comme Average, aux valeurs des colonnes et copie les résultats dans la sortie de la transformation. Outre les fonctions d'agrégation, cette transformation propose la clause GROUP BY qui permet de spécifier des groupes auxquels appliquer l'agrégation.  
  
## <a name="operations"></a>Opérations  
 La transformation d'agrégation prend en charge les opérations suivantes.  
  
|Opération|Description|  
|---------------|-----------------|  
|Regrouper par|Divise les datasets en groupes. Les colonnes contenant tout type de données peuvent être utilisées pour le regroupement. Pour plus d’informations, consultez [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql).|  
|SUM|Additionne les valeurs dans une colonne. Seules les colonnes dont les données sont numériques peuvent être additionnées. Pour plus d’informations, consultez [SUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql).|  
|Average|Retourne la moyenne des valeurs d'une colonne. La moyenne ne peut être calculée que sur les colonnes dont les données sont numériques. Pour plus d’informations, consultez [AVG &#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql).|  
|Count|Retourne le nombre d'éléments figurant dans un groupe. Pour plus d’informations, consultez [COUNT &#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql).|  
|Count distinct|Retourne le nombre de valeurs non NULL uniques d'un groupe.|  
|Minimum|Renvoie la valeur minimale figurant dans un groupe. Pour plus d’informations, consultez [MIN &#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql). À la différence de la fonction Transact-SQL MIN, cette opération peut être utilisée uniquement avec des données de type numérique, date et heure.|  
|Maximale|Renvoie la valeur maximale figurant dans un groupe. Pour plus d’informations, consultez [MAX &#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql). À la différence de la fonction Transact-SQL MAX, cette opération peut être utilisée uniquement avec des données de type numérique, date et heure.|  
  
 La transformation d'agrégation traite les valeurs null de la même manière que le moteur de base de données relationnelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Ce comportement est défini dans la norme SQL-92. Les règles suivantes s’appliquent :  
  
-   Dans une clause GROUP BY, les valeurs NULL sont traitées comme toute autre valeur de colonne. Si la colonne de regroupement contient plusieurs valeurs null, ces valeurs sont placées dans un seul groupe.  
  
-   Dans les fonctions COUNT (nom de colonne) et COUNT (nom de colonne DISTINCT), les valeurs NULL sont ignorées et le résultat ne tient pas compte des lignes contenant des valeurs NULL dans la colonne nommée.  
  
-   Dans la fonction COUNT (*), toutes les lignes sont comptées, y compris celles contenant des valeurs NULL.  
  
## <a name="big-numbers-in-aggregates"></a>Nombres élevés dans les agrégats  
 Une colonne peut contenir des valeurs numériques nécessitant une attention particulière en raison de leur grandeur ou de leur précision. La transformation d’agrégation inclut la propriété IsBig que vous pouvez définir sur les colonnes de sortie pour appeler un traitement spécial des nombres élevés ou de grande précision. Si la valeur d’une colonne dépasse 4 milliards ou si une précision plus grande que le type de données float est requise, vous devez affecter la valeur 1 à IsBig.  
  
 Le fait d’affecter la valeur 1 à IsBig affecte la sortie de la transformation d’agrégation de la manière suivante :  
  
-   Le type de données DT_R8 est utilisé à la place du type de données DT_R4.  
  
-   Les résultats de l'opération Count sont stockés en tant que type de données DT_UI8.  
  
-   Les résultats de l'opération Comptage de valeurs sont stockés en tant que type de données DT_UI4.  
  
> [!NOTE]  
>  Vous ne pouvez pas affecter la valeur 1 à IsBig pour les colonnes utilisées avec les opérations GROUP BY, Maximum ou Minimum.  
  
## <a name="performance-considerations"></a>Considérations relatives aux performances  
 La transformation d'agrégation comprend un ensemble de propriétés que vous pouvez définir pour améliorer ses performances.  
  
-   Quand vous effectuez une opération **Group by** , définissez les propriétés Keys ou KeysScale du composant et les sorties du composant. Grâce à Keys, vous pouvez spécifier le nombre exact de clés que la transformation doit normalement traiter. (Dans ce contexte, Keys fait référence au nombre de groupes attendus d’une opération **Group by** .) Grâce à KeysScale, vous pouvez spécifier un nombre approximatif de clés. Quand vous spécifiez une valeur appropriée pour Keys ou KeyScale, vous améliorez les performances car la transformation peut allouer la mémoire adéquate pour les données mises en cache par la transformation.  
  
-   Quand vous effectuez une opération **Comptage de valeurs** , définissez les propriétés CountDistinctKeys ou CountDistinctScale du composant. Grâce à CountDistinctKeys, vous pouvez indiquer le nombre exact de clés que la transformation doit normalement traiter pour une opération Count Distinct. (Dans ce contexte, CountDistinctKeys fait référence au nombre de valeurs distinctes attendues d’une opération **Comptage de valeurs** .) La propriété CountDistinctScale permet d’indiquer un nombre approximatif de clés pour une opération Count Distinct. Quand vous spécifiez une valeur appropriée pour CountDistinctKeys ou CountDistinctScale, vous améliorez les performances car la transformation peut allouer la mémoire adéquate pour les données mises en cache par la transformation.  
  
## <a name="aggregate-transformation-configuration"></a>Configuration de la transformation d'agrégation  
 La transformation d'agrégation est configurée au niveau de la transformation, de la sortie et de la colonne.  
  
-   Au niveau de la transformation, vous configurez la transformation d'agrégation pour les performances en spécifiant les valeurs suivantes :  
  
    -   Nombre de groupes attendus d’une opération **Group by**  
  
    -   Nombre de valeurs distinctes attendues d’une opération **Count Distinct**  
  
    -   Pourcentage par lequel la mémoire peut être étendue pendant l'agrégation.  
  
     La transformation d'agrégation peut également être configurée de manière à générer un avertissement au lieu d'échouer lorsque la valeur d'un diviseur est zéro.  
  
-   Au niveau de la sortie, vous configurez la transformation d’agrégation pour les performances en spécifiant le nombre de groupes attendus d’une opération **Group by** . La transformation d'agrégation prend en charge plusieurs sorties ; chacune pouvant être configurée différemment.  
  
-   Au niveau de la colonne, vous spécifiez les valeurs suivantes :  
  
    -   agrégation que la colonne effectue ;  
  
    -   options de comparaison de l'agrégation.  
  
 Vous pouvez également configurer la transformation d'agrégation pour les performances en spécifiant les valeurs suivantes :  
  
-   Nombre de groupes attendus d’une opération **Group by** dans la colonne  
  
-   Nombre de valeurs distinctes attendues d’une opération **Count Distinct** dans la colonne  
  
 Vous pouvez également identifier des colonnes en tant que IsBig si une colonne contient des valeurs numériques élevées ou de grande précision.  
  
 La transformation d'agrégation est asynchrone, ce qui signifie qu'elle ne consomme pas les données et ne les publie pas ligne par ligne. Au lieu de cela, elle consomme tout l'ensemble de lignes, effectue les regroupements et les agrégations, puis publie les résultats.  
  
 Cette transformation ne transmet aucune colonne, mais en crée de nouvelles dans le flux de données pour les données qu'elle publie. Seules les colonnes d'entrée auxquelles des fonctions d'agrégation s'appliquent ou les colonnes d'entrée que la transformation utilise pour le regroupement sont copiées dans la sortie de la transformation. Par exemple, l’entrée d’une transformation d’agrégation peut contenir trois colonnes : **PaysRegion**, **Ville**et **Population**. La transformation effectue un regroupement à partir de la colonne **PaysRegion** et applique la fonction Sum à la colonne **Population** . La sortie n’inclut donc pas la colonne **Ville** .  
  
 Vous pouvez également ajouter plusieurs sorties à la transformation d'agrégation et diriger chaque agrégation vers une sortie différente. Par exemple, si la transformation d’agrégation applique les fonctions Sum et Average, chaque agrégation peut être dirigée vers une sortie différente.  
  
 Vous pouvez appliquer plusieurs agrégations à une même colonne d'entrée. Par exemple, si vous souhaitez calculer la somme et la moyenne d’une colonne d’entrée nommée **Ventes**, vous pouvez configurer la transformation pour qu’elle applique les fonctions Sum et Average à la colonne **Ventes** .  
  
 La transformation d'agrégation comporte une entrée et une ou plusieurs sorties. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation d’agrégation** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de transformation d’agrégation &#40;onglet Agrégations&#41;](../../aggregate-transformation-editor-aggregations-tab.md)  
  
-   [Éditeur de transformation d’agrégation &#40;onglet Avancé&#41;](../../aggregate-transformation-editor-advanced-tab.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Agréger les valeurs dans un dataset à l'aide de la transformation d'agrégation](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 [Agréger les valeurs dans un dataset à l'aide de la transformation d'agrégation](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Transmission de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
