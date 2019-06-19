---
title: StreamOpenOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 091c640ab09cf70cff5e6f7ce3d7bf1dc9dd34ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710717"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Spécifie les options pour l’ouverture une [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet. Les valeurs peuvent être combinées avec une opération OR.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Ouvre le **Stream** objet en mode asynchrone.|  
|**adOpenStreamFromRecord**|4|Identifie le contenu de la *Source* paramètre soit déjà ouvert [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet. Le comportement par défaut consiste à traiter *Source* comme une URL qui pointe directement vers un nœud dans une structure arborescente. Le flux par défaut associé à ce nœud est ouvert.|  
|**adOpenStreamUnspecified**|-1|Valeur par défaut. Spécifie l’ouverture du **Stream** objet avec les options par défaut.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
