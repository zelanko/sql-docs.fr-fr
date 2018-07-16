---
title: Ensemble de lignes DISCOVER_LOCATIONS | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 90fa167102e9e5a5c8a4ad916bb921205347f1c6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284435"
---
# <a name="discoverlocations-rowset"></a>Ensemble de lignes DISCOVER_LOCATIONS
  Retourne des informations sur le contenu d'un fichier de sauvegarde. Vous devez disposer de l'autorisation requise pour accéder à l'emplacement du fichier de sauvegarde.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_LOCATIONS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Obligatoire, voir ci-dessous.|Emplacement du fichier de sauvegarde.|  
|`LOCATION_PARTITION_OBJECTPATH`|`DBTYPE_WSTR`||Chemin d'accès à la partition en fonction du dossier de données.|  
|`LOCATION_PARTITION_DATASOURCEID`|`DBTYPE_WSTR`||ID de source de données utilisé pour le traitement de la partition.|  
|`LOCATION_PARTITION_DATASOURCENAME`|`DBTYPE_WSTR`||Nom de la source de données utilisée pour le traitement.|  
|`LOCATION_PARTITION_NAME`|`DBTYPE_WSTR`||Nom de la partition.|  
|`LOCATION_PARTITION_SIZE`|`DBTYPE_WSTR`||Taille approximative de la partition.|  
|`LOCATION_CONNECTION_STRING`|`DBTYPE_WSTR`||Chaîne de connexion pour la source de données utilisée dans le traitement.|  
|`LOCATION_PARTITION_FOLDER`|`DBTYPE_WSTR`||Emplacement d'origine de cette partition lorsque le fichier de sauvegarde a été généré.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_LOCATIONS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Requis|  
|`LOCATION_PASSWORD PF_DBTYPE`|`DBTYPE_WSTR`|Obligatoire s'il a été spécifié pendant la sauvegarde. Cette restriction n'est pas utilisée pour limiter les lignes retournées. Elle est utilisée pour fournir le mot de passe en vue d'accéder à l'emplacement.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Emplacements|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
