---
title: Ensemble de lignes DISCOVER_INSTANCES | Documents Microsoft
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
apiname: DISCOVER_INSTANCES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_INSTANCES rowset
ms.assetid: e0842e63-089d-468d-869f-634da343d9fb
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4f5bcf5b090b1fb011ce4676b320291515044fd7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="discoverinstances-rowset"></a>Ensemble de lignes DISCOVER_INSTANCES
  Décrit les instances sur le serveur.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_INSTANCES** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**NOM_INSTANCE**|**DBTYPE_WSTR**||Nom de l'instance.|  
|**INSTANCE_PORT_NUMBER**|**DBTYPE_I4**||Numéro de port sur lequel l'instance écoute.|  
|**INSTANCE_STATE**|**DBTYPE_I4**||État de l'instance du serveur :<br /><br /> **Démarré**<br /><br /> **Arrêté**<br /><br /> **Démarrage de**<br /><br /> **L’arrêt**<br /><br /> **Suspendu**|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_INSTANCES** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**NOM_INSTANCE**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
