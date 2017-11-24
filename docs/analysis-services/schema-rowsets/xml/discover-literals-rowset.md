---
title: Ensemble de lignes DISCOVER_LITERALS | Documents Microsoft
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
apiname: DISCOVER_LITERALS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 93653c72c4259c5da489df045ef362e7ff6041be
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="discoverliterals-rowset"></a>Ensemble de lignes DISCOVER_LITERALS
  Retourne des informations sur les littéraux pris en charge par le fournisseur XMLA (XML for Analysis) [!INCLUDE[msCoName](../../../includes/msconame-md.md)], y compris les types de données et les valeurs.  
  
 Si vous appelez le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) méthode avec la **DISCOVER_LITERALS** valeur d’énumération dans le [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) élément, le **Discover** méthode retourne la **DISCOVER_LITERALS** ensemble de lignes.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **DISCOVER_LITERALS** ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**LiteralName**|**DBTYPE_WSTR**||Nom du littéral décrit dans la ligne.<br /><br /> Par exemple : **DBLITERAL_LIKE_PERCENT**|  
|**LiteralValue**|**DBTYPE_WSTR**||Valeur littérale réelle.<br /><br /> Par exemple, si **LiteralName** est **DBLITERAL_LIKE_PERCENT** et le caractère de pourcentage (**%**) correspond à zéro ou plusieurs caractères dans une clause LIKE, la valeur de la **LiteralValue** colonne est «**%**».|  
|**LiteralInvalidChars**|**DBTYPE_WSTR**||Caractères qui ne sont pas valides dans le littéral.<br /><br /> Par exemple, si les noms de table peuvent contenir la valeur de l’autre chose qu’un caractère numérique, cette chaîne est «**0123456789**».|  
|**LiteralInvalidStartingChars**|**DBTYPE_WSTR**||Caractères qui ne sont pas valides comme premier caractère dans le littéral. Si le littéral peut commencer par n’importe quel caractère valide, il s’agit **null**.|  
|**LiteralMaxLength**|**DBTYPE_I4**||Nombre maximal de caractères du littéral. Si la colonne ne possède pas de longueur maximale ou si elle est inconnue, la valeur est -1.|  
|**LiteralNameEnumValue**|**DBTYPE_I4**|||  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le **DISCOVER_LITERALS** ensemble de lignes peut être restreint sur les colonnes dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**LiteralName**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Ensemble de lignes DISCOVER_KEYWORDS &#40; XMLA &#41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
