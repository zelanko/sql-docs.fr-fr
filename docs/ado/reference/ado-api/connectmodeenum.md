---
title: ConnectModeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectModeEnum
helpviewer_keywords:
- ConnectModeEnum enumeration [ADO]
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: debf6f9dc4ac1326caf9fbf32b65f15f34a19094
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933454"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Spécifie les autorisations disponibles pour la modification des données dans une [connexion](../../../ado/reference/ado-api/connection-object-ado.md), l’ouverture d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md)ou la spécification de valeurs pour la propriété [mode](../../../ado/reference/ado-api/mode-property-ado.md) des objets **Record** et [Stream](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|Indique des autorisations en lecture seule.|  
|**adModeReadWrite**|3|Indique des autorisations de lecture/écriture.|  
|**adModeRecursive**|0x400000|Utilisé conjointement avec les autres * \*valeurs ShareDeny\* * (**adModeShareDenyNone**, **adModeShareDenyWrite**ou **adModeShareDenyRead**) pour propager des restrictions de partage à tous les sous-enregistrements de l' **enregistrement**actif. Elle n’a aucun effet si l' **enregistrement** n’a pas d’enfants. Une erreur d’exécution est générée si elle est utilisée avec **adModeShareDenyNone** uniquement. Toutefois, il peut être utilisé avec **adModeShareDenyNone** lorsqu’il est combiné à d’autres valeurs. Par exemple, vous pouvez utiliser «**adModeRead** » ou « **adModeShareDenyNone** » ou « **adModeRecursive**».|  
|**adModeShareDenyNone**|16|Permet à d’autres utilisateurs d’ouvrir une connexion avec toutes les autorisations. Aucun accès en lecture ou en écriture ne peut être refusé à d'autres personnes.|  
|**adModeShareDenyRead**|4|Empêche les autres utilisateurs d’ouvrir une connexion avec des autorisations de lecture.|  
|**adModeShareDenyWrite**|8|Empêche les autres utilisateurs d’ouvrir une connexion avec des autorisations d’écriture.|  
|**adModeShareExclusive**|12|Empêche les autres utilisateurs d’ouvrir une connexion.|  
|**adModeUnknown**|0|valeur par défaut. Indique que les autorisations n’ont pas encore été définies ou ne peuvent pas être déterminées.|  
|**adModeWrite**|2|Indique des autorisations en écriture seule.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.ConnectMode.READ|  
|AdoEnums.ConnectMode.READWRITE|  
|(Il n’existe aucun équivalent de AdoEnums. ConnectMode. Recursive)|  
|AdoEnums.ConnectMode.SHAREDENYNONE|  
|AdoEnums.ConnectMode.SHAREDENYREAD|  
|AdoEnums.ConnectMode.SHAREDENYWRITE|  
|AdoEnums.ConnectMode.SHAREEXCLUSIVE|  
|AdoEnums.ConnectMode.UNKNOWN|  
|AdoEnums.ConnectMode.WRITE|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Mode, propriété (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Open, méthode (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Open, méthode (Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
