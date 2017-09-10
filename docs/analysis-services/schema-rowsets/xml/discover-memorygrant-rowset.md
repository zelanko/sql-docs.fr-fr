---
title: Ensemble de lignes DISCOVER_MEMORYGRANT | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: d254e42d-9918-47ce-b6df-47f1f0b432dd
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ba8bbb7752557c845899c587a39c9ceef357d578
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="discovermemorygrant-rowset"></a>DISCOVER_MEMORYGRANT, ensemble de lignes
  Retourne la liste des allocations de quotas de mémoire interne qui sont prises par les travaux en cours d'exécution sur le serveur. Pour savoir si un travail exécute sur le serveur, utilisez `Select * from $System.Discover_Jobs`.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_MEMORYGRANT** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction| Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MEMORY_ID**|**DBTYPE_I8**||Nombre qui identifie l'allocation de quota de mémoire. Unique dans le contexte d'une demande DISCOVER_MEMORYGRANT unique.|  
|**SPID**|**DBTYPE_I4**|Requis|SPID, que vous pouvez obtenir en exécutant `Select * from $System.Discover_Sessions`.|  
|**CreationTime**|**DBTYPE_I8 DBTYPE_DBTIMESTAMP**||Heure à laquelle le quota a été accordé.|  
|**LastRequestTime**|**DBTYPE_DBTIMESTAMP**||Heure de dernière modification de la demande de quota.|  
|**MemoryUsed**|**DBTYPE_I4**||Quantité de mémoire utilisée en association avec le quota.|  
|**MemoryGranted**|**DBTYPE_I4**||Quantité de mémoire allouée pour le travail qui obtient le quota de mémoire.|  
|**Bloqué**|**DBTYPE_BOOL**||Valeur booléenne qui indique le statut de blocage du travail. True indique que le travail est bloqué et attend qu'un autre travail libère un quota suffisant pour satisfaire sa demande de quota. False indique que le travail a reçu son quota et peut s'exécuter.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd23-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|MemoryGrant|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
