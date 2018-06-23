---
title: Query, élément (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Query Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords:
- Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e01c14cb889a7d2953c98d8dfeee3bb89eee344e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051342"
---
# <a name="query-element-xmla"></a>Élément Query (XMLA)
  Contient une requête dans le [requêtes](queries-element-xmla.md) collection utilisée par le [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) commande pendant l’optimisation de l’utilisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Requêtes](queries-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La commande `DesignAggregations` prend en charge l'optimisation basée sur l'utilisation en incluant un ou plusieurs éléments `Query` dans la collection `Queries` de la commande. Chaque `Query` élément représente une requête d’objectif que le processus de conception utilise pour définir des agrégations qui visent les requêtes fréquemment utilisées. Vous pouvez spécifier vos propres requêtes d’objectif, ou vous pouvez utiliser les informations stockées par une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] dans le journal des requêtes pour récupérer les informations les plus fréquemment des requêtes utilisées.  
  
 Si vous concevez des agrégations itérative, il vous suffit de passer des requêtes d’objectif dans la première `DesignAggregations` commande car le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance stocke ces requêtes d’objectif et les utilise pendant les `DesignAggregations` commandes. Une fois les requêtes d'objectif passées dans la première commande `DesignAggregations` d'un procédé itératif, toute commande `DesignAggregations` suivante qui contient des requêtes d'objectif dans la propriété `Queries` génère une erreur.  
  
 L'élément `Query` contient une valeur délimitée par des virgules qui renferme les arguments suivants :  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Fréquence*  
 Un facteur de pondération qui correspond au nombre de fois que la requête a été exécutée antérieurement. Si le `Query` élément représente une requête, le *fréquence* valeur représente le facteur de pondération utilisé par le processus de conception pour évaluer la requête. À mesure que la valeur de la fréquence s'accroît, le poids associé à la requête pendant le processus de conception augmente.  
  
 *Jeu de données*  
 Une chaîne numérique qui spécifie quels attributs d'une dimension doivent être inclus dans la requête. Cette chaîne doit comporter autant de caractères que la dimension compte d'attributs. Zéro (0) indique que l'attribut à la position ordinale spécifiée n'est pas inclus dans la requête pour la dimension spécifiée, alors qu'un (1) indique que l'attribut à la position ordinale spécifiée est inclus dans la requête pour la dimension spécifiée.  
  
 Par exemple, la chaîne  « 011 » se rapporte à une requête concernant une dimension à trois attributs, dont le deuxième et le troisième sont inclus dans la requête.  
  
> [!NOTE]  
>  Certains attributs, qualifiés d'exclus, ne sont pas pris en compte dans le dataset. Pour plus d’informations sur les attributs exclus, consultez [propriétés (XMLA)](query-element-xmla.md).  
  
 Chaque dimension du groupe de mesures qui contient la conception d’agrégation est représentée par un *Dataset* valeur dans le `Query` élément. L'ordre des valeurs *Dataset* doit correspondre à celui des dimensions incluses dans le groupe de mesures.  
  
## <a name="see-also"></a>Voir aussi  
 [Conception d’agrégations &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  