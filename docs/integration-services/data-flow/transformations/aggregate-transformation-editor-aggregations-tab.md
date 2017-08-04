---
title: "Éditeur de Transformation (onglet agrégations) d’agrégation | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6e7bf78662f021ae3c6ff776635035feea985b12
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="aggregate-transformation-editor-aggregations-tab"></a>Éditeur de transformation d'agrégation (onglet Agrégations)
  Utilisez l’onglet **Agrégations** de la boîte de dialogue **Éditeur de transformation d’agrégation** pour spécifier les colonnes destinées à l’agrégation et les propriétés de cette agrégation. Vous pouvez appliquer plusieurs agrégations. Ce type de transformation ne génère pas d'erreur de sortie.  
  
> [!NOTE]  
>  Les options concernant le nombre et l’échelle de clés d’une part et le nombre et l’échelle de clés distinctes d’autre part s’appliquent au niveau du composant quand ces options sont indiquées sous l’onglet **Avancé** , au niveau de la sortie quand elles sont précisées dans l’affichage avancé de l’onglet **Agrégations** ou encore au niveau des colonnes quand elles sont spécifiées dans la liste de colonnes se trouvant dans la partie inférieure de l’onglet **Agrégations** .  
>   
>  Dans la transformation d’agrégation, **Clés** et **Échelle de clé** font référence au nombre de groupes attendus d’une opération **Group by** . **Nombre de clés distinctes** et **Échelle de nombre des valeurs distinctes** font référence au nombre de valeurs distinctes attendues d’une opération **Comptage de valeurs** .  
  
 Pour en savoir plus sur la transformation d’agrégation, consultez [Transformation d’agrégation](../../../integration-services/data-flow/transformations/aggregate-transformation.md).  
  
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
 Si vous sélectionnez **Group by**, permet d’utiliser les cases à cocher afin de contrôler le mode d’évaluation de la comparaison effectuée par la transformation. Pour plus d’informations sur les options de comparaison de chaînes, consultez [Comparaison des données chaînes](../../../integration-services/data-flow/comparing-string-data.md).  
  
 **Count Distinct Scale**  
 Permet éventuellement de spécifier le nombre approximatif de valeurs distinctes que l'agrégation peut écrire. Par défaut, la valeur de cette option est **Non spécifié**. Si la valeur des propriétés **CountDistinctScale** et **CountDistinctKeys** sont toutes deux précisées, celle de la propriété **CountDistinctKeys** prévaut alors.  
  
|Value|Description|  
|-----------|-----------------|  
|Non spécifié|La propriété **CountDistinctScale** n’est pas utilisée.|  
|Faible|L'agrégation peut écrire environ 500 000 valeurs distinctes.|  
|Moyenne|L’agrégation peut écrire environ 5 000 000 de valeurs distinctes.|  
|Élevée|L'agrégation peut écrire plus de 25 000 000 valeurs distinctes.|  
  
 **Count Distinct Keys**  
 Permet de spécifier éventuellement le nombre exact de valeurs distinctes que l'agrégation peut écrire. Si la valeur des propriétés **CountDistinctScale** et **CountDistinctKeys** sont toutes deux précisées, celle de la propriété **CountDistinctKeys** prévaut alors.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de Transformation d’agrégation &#40; Onglet Avancé &#41;](../../../integration-services/data-flow/transformations/aggregate-transformation-editor-advanced-tab.md)   
 [Agréger les valeurs dans un jeu de données à l’aide de la Transformation d’agrégation](../../../integration-services/data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
