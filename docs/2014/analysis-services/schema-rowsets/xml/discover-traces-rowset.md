---
title: Ensemble de lignes DISCOVER_TRACES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f50b7fa39bca030c7864f75b856b8e7ee2953de
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207969"
---
# <a name="discovertraces-rowset"></a>DISCOVER_TRACES, ensemble de lignes
  Fournit des informations sur les traces qui sont actuellement actives sur le serveur.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_TRACES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Description|  
|-----------------|--------------------|-----------------|  
|`TraceID`|`DBTYPE_WSTR`|ID de trace.|  
|`TraceName`|`DBTYPE_WSTR`|Nom de la trace.|  
|`LogFileName`|`DBTYPE_WSTR`|Nom du fichier journal de traces.|  
|`LogFileSize`|`DBTYPE_I4`|Taille du fichier journal de traces.|  
|`LogFileRollover`|`DBTYPE_BOOL`|Si true, indique que le fichier journal doit être substitué ; sinon false.|  
|`AutoRestart`|`DBTYPE_BOOL`|Si true, indique que l'option de redémarrage automatique est activée ; sinon false.|  
|`CreationTime`|`DBTYPE_TIME`|Date et heure de création de la trace.|  
|`StopTime`|`DBTYPE_TIME`|Heure d'arrêt d'une trace.|  
|`Type`|`PF_DBTYPE_WSTR`|Type de trace.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_TRACES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|`DBTYPE_I4`|Facultatif.|  
|`Type`|WSTR|Facultatif.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACES|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
