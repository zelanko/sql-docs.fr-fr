---
title: Éditeur de Transformation (onglet agrégations) d’agrégation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: db633e9afa480d03b31cf02a84db2813b1e30516
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771945"
---
# <a name="aggregate-transformation-editor-aggregations-tab"></a>Éditeur de transformation d'agrégation (onglet Agrégations)
  Utilisez l’onglet **Agrégations** de la boîte de dialogue **Éditeur de transformation d’agrégation** pour spécifier les colonnes destinées à l’agrégation et les propriétés de cette agrégation. Vous pouvez appliquer plusieurs agrégations. Ce type de transformation ne génère pas d'erreur de sortie.  
  
> [!NOTE]  
>  Les options concernant le nombre et l’échelle de clés d’une part et le nombre et l’échelle de clés distinctes d’autre part s’appliquent au niveau du composant quand ces options sont indiquées sous l’onglet **Avancé** , au niveau de la sortie quand elles sont précisées dans l’affichage avancé de l’onglet **Agrégations** ou encore au niveau des colonnes quand elles sont spécifiées dans la liste de colonnes se trouvant dans la partie inférieure de l’onglet **Agrégations** .  
>   
>  Dans la transformation d’agrégation, **Clés** et **Échelle de clé** font référence au nombre de groupes attendus d’une opération **Regrouper par** . **Nombre de clés distinctes** et **Échelle de nombre des valeurs distinctes** font référence au nombre de valeurs distinctes attendues d’une opération **Comptage de valeurs** .  
  
 Pour en savoir plus sur la transformation d’agrégation, consultez [Transformation d’agrégation](data-flow/transformations/aggregate-transformation.md).  
  
## <a name="options"></a>Options  
 **Avancé / Simple**  
 Permet d'afficher ou de masquer les options permettant de configurer plusieurs agrégations dans le cas de sorties multiples. Par défaut, les options avancées sont masquées.  
  
 **Nom d'agrégation**  
 Dans l'écran Avancé, permet d'attribuer un nom convivial à l'agrégation.  
  
 **Grouper par colonnes**  
 Dans l’écran Avancé, permet de sélectionner les colonnes afin de regrouper les éléments d’après la liste **Colonnes d’entrée disponibles** , comme décrit ci-dessous.  
  
 **Échelle de clé**  
 Dans l'écran Avancé, permet de spécifier aussi éventuellement le nombre de clés adéquat que l'agrégation peut écrire. Par défaut, la valeur de cette option est **Non spécifié**. Si la valeur des propriétés **Échelle de clé** et **Clés** sont toutes deux définies, c’est celle de la propriété **Clés** qui prévaut.  
  
|Value|Description|  
|-----------|-----------------|  
|Non spécifié|La propriété Échelle de clé n'est pas utilisée.|  
|Faible|L’agrégation peut écrire environ 500 000 clés.|  
|Moyenne|L'agrégation peut écrire environ 5 000 000 clés.|  
|Élevée|L'agrégation peut écrire plus de 25 000 000 clés.|  
  
 **Clés**  
 Dans l'écran Avancé, permet d'indiquer éventuellement le nombre exact de clés que l'agrégation peut écrire. Si la valeur des propriétés **Échelle de clé** et **Clés** sont toutes deux précisées, celle de la propriété **Clés** prévaut alors.  
  
 **Colonnes d’entrée disponibles**  
 Permet de sélectionner les colonnes dans la liste des colonnes d'entrée disponibles en cochant ou décochant les cases du tableau.  
  
 **Colonne d'entrée**  
 Permet de sélectionner des colonnes dans la liste des colonnes d'entrée disponibles.  
  
 **Alias de sortie**  
 Permet de saisir un alias pour chaque colonne. Par défaut, il s'agit du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
 **Opération**  
 Permet de choisir dans la liste parmi les opérations disponibles, d'après le tableau suivant.  
  
|Opération|Description|  
|---------------|-----------------|  
|**GroupBy**|Divise les datasets en groupes. Les colonnes incluant tout type de données peuvent être utilisées pour le regroupement. Pour plus d'informations, consultez GROUP BY.|  
|**Sum**|Additionne les valeurs dans une colonne. Seules les colonnes dont les données sont numériques peuvent être additionnées. Pour plus d'informations, consultez SUM.|  
|**Moyenne**|Retourne la moyenne des valeurs d'une colonne. La moyenne ne peut être calculée que sur les colonnes dont les données sont numériques. Pour plus d'informations, consultez AVG.|  
|**Compter**|Retourne le nombre d'éléments figurant dans un groupe. Pour plus d'informations, consultez COUNT.|  
|**CountDistinct**|Retourne le nombre de valeurs non NULL uniques d'un groupe. Pour plus d'informations, consultez COUNT et Distinct.|  
|**Minimum**|Renvoie la valeur minimale figurant dans un groupe. Cette opération se restreint aux données numériques.|  
|**Maximum**|Renvoie la valeur maximale figurant dans un groupe. Cette opération se restreint aux données numériques.|  
  
 **Indicateurs de comparaison**  
 Si vous sélectionnez **Group by**, permet d’utiliser les cases à cocher afin de contrôler le mode d’évaluation de la comparaison effectuée par la transformation. Pour plus d’informations sur les options de comparaison de chaînes, consultez [Comparaison des données chaînes](data-flow/comparing-string-data.md).  
  
 **Count Distinct Scale**  
 Permet éventuellement de spécifier le nombre approximatif de valeurs distinctes que l'agrégation peut écrire. Par défaut, la valeur de cette option est **Non spécifié**. Si les deux `CountDistinctScale` et **CountDistinctKeys** sont spécifiés, **CountDistinctKeys** est prioritaire.  
  
|Value|Description|  
|-----------|-----------------|  
|Non spécifié|La propriété `CountDistinctScale` n'est pas utilisée.|  
|Faible|L'agrégation peut écrire environ 500 000 valeurs distinctes.|  
|Moyenne|L’agrégation peut écrire environ 5 000 000 de valeurs distinctes.|  
|Élevée|L'agrégation peut écrire plus de 25 000 000 valeurs distinctes.|  
  
 **Count Distinct Keys**  
 Permet de spécifier éventuellement le nombre exact de valeurs distinctes que l'agrégation peut écrire. Si les deux `CountDistinctScale` et **CountDistinctKeys** sont spécifiés, **CountDistinctKeys** est prioritaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation d’agrégation &#40;onglet Avancé&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md)   
 [Agréger les valeurs dans un dataset à l'aide de la transformation d'agrégation](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
