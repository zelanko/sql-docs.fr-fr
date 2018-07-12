---
title: Ensemble de lignes DISCOVER_LOCKS | Microsoft Docs
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
helpviewer_keywords:
- DISCOVER_LOCKS rowset
ms.assetid: dea48167-212c-40b7-a416-434042a1b697
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4458d9dac98fd35d54ff35c0d1d524a92b576ba5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167596"
---
# <a name="discoverlocks-rowset"></a>Ensemble de lignes DISCOVER_LOCKS
  Fournit des informations sur les verrous actuellement en place sur le serveur.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_LOCKS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`LOCK_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||Heure UTC du serveur au moment où le verrou a été demandé.|  
|`LOCK_GRANT_TIME`|`DBTYPE_DBTIMESTAMP`||Heure UTC du serveur au moment où le verrou a été accordé sur la ressource.|  
|`LOCK_ID`|`DBTYPE_GUID`||Identificateur unique du verrou, tel qu'un GUID.|  
|`LOCK_OBJECT_ID`|`DBTYPE_WSTR`||Identificateur unique de l'objet actuellement verrouillé.|  
|`LOCK_STATUS`|`DBTYPE_I4`||État du verrou.<br /><br /> 0 signifie « Attente de verrouillage de l'objet ».<br /><br /> 1 signifie « Verrou accordé ».|  
|`LOCK_TRANSACTION_ID`|`DBTYPE_GUID`||Identificateur unique de la transaction, tel qu'un GUID.|  
|`LOCK_TYPE`|`DBTYPE_I4`||Masque de bits des types de verrouillage ; pour plus d'informations, consultez la section Remarques de cette rubrique.|  
|`SPID`|`DBTYPE_I4`||ID de session.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_LOCKS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Facultatif.|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|Facultatif.|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|Facultatif.|  
|LOCK_STATUS|DBTYPE_I4|Facultatif.|  
|LOCK_TYPE|DBTYPE_I4|Facultatif.|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|Facultatif.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="lock-types"></a>Types de verrouillage  
  
|Nom du verrou|Valeur|Description|  
|---------------|-----------|-----------------|  
|LOCK_NONE|0x0000000|Aucun verrou.|  
|LOCK_SESSION_LOCK|0x0000001|Session inactive ; n'interfère pas avec les autres verrous.|  
|LOCK_READ|0x0000002|Verrou de lecture durant le traitement.|  
|LOCK_WRITE|0x0000004|Verrou d'écriture durant le traitement.|  
|LOCK_COMMIT_READ|0x0000008|Verrou de validation, partagé.|  
|LOCK_COMMIT_WRITE|0x0000010|Verrou de validation, exclusif.|  
|LOCK_COMMIT_ABORTABLE|0x0000020|Abandon lors de la validation.|  
|LOCK_COMMIT_INPROGRESS|0x0000040|Validation en cours.|  
|LOCK_INVALID|0x0000080|Verrou non valide.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
