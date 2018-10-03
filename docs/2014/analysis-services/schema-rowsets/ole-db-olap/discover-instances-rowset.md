---
title: Ensemble de lignes DISCOVER_INSTANCES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_INSTANCES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_INSTANCES rowset
ms.assetid: e0842e63-089d-468d-869f-634da343d9fb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a0f716f32898668e019db15aef62e140e9c0d09
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198584"
---
# <a name="discoverinstances-rowset"></a>Ensemble de lignes DISCOVER_INSTANCES
  Décrit les instances sur le serveur.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_INSTANCES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`INSTANCE_NAME`|`DBTYPE_WSTR`||Nom de l'instance.|  
|`INSTANCE_PORT_NUMBER`|`DBTYPE_I4`||Numéro de port sur lequel l'instance écoute.|  
|`INSTANCE_STATE`|`DBTYPE_I4`||État de l'instance du serveur :<br /><br /> -   `Started`<br />-   `Stopped`<br />-   `Starting`<br />-   `Stopping`<br />-   `Paused`|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_INSTANCES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`INSTANCE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
