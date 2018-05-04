---
title: Ensemble de lignes DISCOVER_LOCKS | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_LOCKS rowset
ms.assetid: dea48167-212c-40b7-a416-434042a1b697
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d93f7d578defe5aa10aaa8e1a5f7ac94c3cc05ea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="discoverlocks-rowset"></a>Ensemble de lignes DISCOVER_LOCKS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fournit des informations sur les verrous actuellement en place sur le serveur.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_LOCKS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**LOCK_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||Heure UTC du serveur au moment où le verrou a été demandé.|  
|**LOCK_GRANT_TIME**|**DBTYPE_DBTIMESTAMP**||Heure UTC du serveur au moment où le verrou a été accordé sur la ressource.|  
|**LOCK_ID**|**DBTYPE_GUID**||Identificateur unique du verrou, tel qu'un GUID.|  
|**LOCK_OBJECT_ID**|**DBTYPE_WSTR**||Identificateur unique de l'objet actuellement verrouillé.|  
|**LOCK_STATUS**|**DBTYPE_I4**||État du verrou.<br /><br /> 0 signifie « Attente de verrouillage de l'objet ».<br /><br /> 1 signifie « Verrou accordé ».|  
|**LOCK_TRANSACTION_ID**|**DBTYPE_GUID**||Identificateur unique de la transaction, tel qu'un GUID.|  
|**TYPE DE VERROU**|**DBTYPE_I4**||Masque de bits des types de verrouillage ; pour plus d'informations, consultez la section Remarques de cette rubrique.|  
|**SPID**|**DBTYPE_I4**||ID de session.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_LOCKS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Facultatif.|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|Ce paramètre est facultatif.|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|Ce paramètre est facultatif.|  
|LOCK_STATUS|DBTYPE_I4|Ce paramètre est facultatif.|  
|LOCK_TYPE|DBTYPE_I4|Ce paramètre est facultatif.|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|Ce paramètre est facultatif.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="lock-types"></a>Types de verrouillage  
  
|Nom du verrou|Valeur| Description|  
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
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
