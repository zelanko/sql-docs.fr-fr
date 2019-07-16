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
ms.openlocfilehash: 562e79590a2a5f1f5e9bb609b9a0ad0ea8b2bfd9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928684"
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
