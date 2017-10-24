---
title: ADCPROP_UPDATERESYNC_ENUM | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e5c25ab6802b6a99902c9e52990be80ff14ed6d5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
Spécifie si le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthode est suivie par implicite [Resync](../../../ado/reference/ado-api/resync-method.md) opération de la méthode et dans ce cas, la portée de cette opération.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Appelle **Resync** avec la valeur combinée de tous les autres membres ADCPROP_UPDATERESYNC_ENUM.|  
|**adResyncAutoIncrement**|1|Valeur par défaut. Tente de récupérer la nouvelle valeur d’identité pour les colonnes qui sont automatiquement incrémenté ou générés par la source de données, tels que les champs Microsoft Jet AutoNumber ou les colonnes d’identité de Microsoft SQL Server.|  
|**adResyncConflicts**|2|Appelle **Resync** pour toutes les lignes dans lesquelles l’opération de mise à jour ou de suppression a échoué en raison d’un conflit d’accès concurrentiel.|  
|**adResyncInserts**|8|Appelle **Resync** pour toutes les lignes insérées avec succès. Toutefois, les valeurs des colonnes AutoIncrement ne sont pas resynchronisés. Au lieu de cela, le contenu de lignes nouvellement insérées est resynchronisé en fonction de la valeur de clé primaire existante. Si la clé primaire est une valeur d’auto-incrémentation, **Resync** ne sera pas récupérer le contenu de la ligne concernée. Pour incrémenter automatiquement les valeurs de clé primaire AutoIncrement, appelez **UpdateBatch** avec la valeur combinée **adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|N’appelle pas **Resync**.|  
|**adResyncUpdates**|4|Appelle **Resync** pour toutes les lignes mises à jour avec succès.|  
  
## <a name="applies-to"></a>S'applique à  
 [Mise à jour Resync propriété dynamique (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)

