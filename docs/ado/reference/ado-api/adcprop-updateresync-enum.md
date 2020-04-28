---
title: ADCPROP_UPDATERESYNC_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 82a5473a68303d429794d8b98c4e91293e4e30cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921401"
---
# <a name="adcprop_updateresync_enum"></a>ADCPROP_UPDATERESYNC_ENUM
Spécifie si la méthode [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) est suivie d’une opération de méthode de [resynchronisation](../../../ado/reference/ado-api/resync-method.md) implicite et, le cas échéant, de l’étendue de cette opération.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Appelle **Resync** avec la valeur combinée de tous les autres membres de ADCPROP_UPDATERESYNC_ENUM.|  
|**adResyncAutoIncrement**|1|Par défaut. Tente de récupérer la nouvelle valeur d’identité pour les colonnes qui sont automatiquement incrémentées ou générées par la source de données, telles que les champs de numérotation automatique Microsoft Jet ou les colonnes d’identité Microsoft SQL Server.|  
|**adResyncConflicts**|2|Appelle **Resync** pour toutes les lignes dans lesquelles l’opération de mise à jour ou de suppression a échoué en raison d’un conflit d’accès concurrentiel.|  
|**adResyncInserts**|8|Appelle **Resync** pour toutes les lignes insérées avec succès. Toutefois, les valeurs de colonne AutoIncrement ne sont pas resynchronisées. Au lieu de cela, le contenu des lignes nouvellement insérées est resynchronisé en fonction de la valeur de clé primaire existante. Si la clé primaire est une valeur AutoIncrement, **Resync** ne récupère pas le contenu de la ligne prévue. Pour incrémenter automatiquement les valeurs de clé primaire AutoIncrement, appelez **UpdateBatch** avec la valeur combinée **adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|N’appelle pas **Resync**.|  
|**adResyncUpdates**|4|Appelle **Resync** pour toutes les lignes mises à jour avec succès.|  
  
## <a name="applies-to"></a>S'applique à  
 [Update Resync, propriété dynamique (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
