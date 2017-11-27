---
title: Ensemble de lignes DISCOVER_KEYWORDS (XMLA) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_KEYWORDS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_KEYWORDS rowset
ms.assetid: 99945e53-3a1b-4d7b-9aff-712977db8b2d
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a3b07baa51b0b7dbfcdbb41a782fe4a4cab2f2cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="discoverkeywords-rowset-xmla"></a>Ensemble de lignes DISCOVER_KEYWORDS (XMLA)
  Retourne des informations sur les mots clés réservés par le fournisseur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Si vous appelez la méthode [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) avec la valeur d'énumération **DISCOVER_KEYWORDS** dans l'élément [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) , la méthode **Discover** retourne l'ensemble de lignes **DISCOVER_KEYWORDS** .  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_KEYWORDS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**Mot clé**|**DBTYPE_WSTR**||Liste de tous les mots clés réservés par un fournisseur.<br /><br /> Exemple : **AND**|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_KEYWORDS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**Mot clé**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_LITERALS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)  
  
  
