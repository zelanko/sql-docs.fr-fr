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
manager: jroth
ms.openlocfilehash: 6ae4a8adbadc97ad2ea5e3659187481fa71e81b0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698863"
---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
Spécifie si le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthode est suivie par implicite [Resync](../../../ado/reference/ado-api/resync-method.md) opération de la méthode et dans ce cas, la portée de cette opération.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Appelle **Resync** avec la valeur combinée de tous les autres membres ADCPROP_UPDATERESYNC_ENUM.|  
|**adResyncAutoIncrement**|1|Valeur par défaut. Tente de récupérer la nouvelle valeur d’identité pour les colonnes qui sont automatiquement incrémentées ou générées par la source de données, telles que les champs à numérotation automatique du Jet de Microsoft ou des colonnes d’identité de Microsoft SQL Server.|  
|**adResyncConflicts**|2|Appelle **Resync** pour toutes les lignes dans lequel l’opération update ou delete a échoué en raison d’un conflit d’accès concurrentiel.|  
|**adResyncInserts**|8|Appelle **Resync** pour toutes les lignes insérées avec succès. Toutefois, les valeurs de colonnes AutoIncrement ne sont pas resynchronisées. Au lieu de cela, le contenu des lignes nouvellement insérées est resynchronisé selon la valeur de clé primaire existante. Si la clé primaire est une valeur d’auto-incrémentation, **Resync** ne sont pas récupérer le contenu de la ligne concernée. Pour incrémenter automatiquement les valeurs de clé primaire AutoIncrement, appelez **UpdateBatch** avec la valeur combinée **adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|N’appelle pas **Resync**.|  
|**adResyncUpdates**|4|Appelle **Resync** pour toutes les lignes mises à jour avec succès.|  
  
## <a name="applies-to"></a>S'applique à  
 [Update Resync, propriété dynamique (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
