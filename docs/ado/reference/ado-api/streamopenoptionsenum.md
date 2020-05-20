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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1d61b11ee6fedd4229433570f6b159cccf658853
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759585"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Spécifie les options d’ouverture d’un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) . Les valeurs peuvent être combinées avec une opération OR.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Ouvre l’objet de **flux** en mode asynchrone.|  
|**adOpenStreamFromRecord**|4|Identifie le contenu du paramètre *source* comme étant un objet [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) déjà ouvert. Le comportement par défaut consiste à traiter la *source* comme une URL qui pointe directement vers un nœud dans une arborescence. Le flux par défaut associé à ce nœud est ouvert.|  
|**adOpenStreamUnspecified**|-1|Par défaut. Spécifie l’ouverture de l’objet de **flux** avec les options par défaut.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
