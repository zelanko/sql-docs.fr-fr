---
title: Ensemble de lignes DISCOVER_KEYWORDS (OLE DB pour OLAP) | Documents Microsoft
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
- DISCOVER_KEYWORDS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_KEYWORDS rowset
ms.assetid: 70cc680d-9530-469b-8a61-4e6779aec17a
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fb62e984a810f636a22abf733809bfafc91f2d16
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152713"
---
# <a name="discoverkeywords-rowset-ole-db-for-olap"></a>Ensembles de lignes DISCOVER_KEYWORDS (OLE DB pour OLAP)
  Énumère une liste de mots réservés par le fournisseur.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes DISCOVER_KEYWORDS contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`Keyword`|`DBTYPE_WSTR`||Mot clé réservé.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes DISCOVER_KEYWORDS peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`Keyword`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  