---
title: Ensemble de lignes DISCOVER_TRACES | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2eaf3708434961840620a71ffdcaf898b5124301
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="discovertraces-rowset"></a>DISCOVER_TRACES, ensemble de lignes
  Fournit des informations sur les traces qui sont actuellement actives sur le serveur.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_TRACES** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type| Description|  
|-----------------|--------------------|-----------------|  
|**TraceID**|**DBTYPE_WSTR**|ID de trace.|  
|**Trace**|**DBTYPE_WSTR**|Nom de la trace.|  
|**LogFileName**|**DBTYPE_WSTR**|Nom du fichier journal de traces.|  
|**LogFileSize**|**DBTYPE_I4**|Taille du fichier journal de traces.|  
|**LogFileRollover**|**DBTYPE_BOOL**|Si true, indique que le fichier journal doit être substitué ; sinon false.|  
|**Redémarrage automatique**|**DBTYPE_BOOL**|Si true, indique que l'option de redémarrage automatique est activée ; sinon false.|  
|**CreationTime**|**DBTYPE_TIME**|Date et heure de création de la trace.|  
|**StopTime**|**DBTYPE_TIME**|Heure d'arrêt d'une trace.|  
|**Type**|**PF_DBTYPE_WSTR**|Type de trace.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_TRACES** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|**DBTYPE_I4**|Ce paramètre est facultatif.|  
|**Type**|WSTR|Facultatif.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|Chaîne|DISCOVER_TRACES|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

