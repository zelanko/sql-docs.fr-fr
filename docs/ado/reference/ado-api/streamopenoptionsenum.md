---
title: StreamOpenOptionsEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 268d495d2163d03244a6bec57762b93a26ab32ea
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Spécifie les options pour l’ouverture un [flux](../../../ado/reference/ado-api/stream-object-ado.md) objet. Les valeurs peuvent être combinées avec une opération OR.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Ouvre le **flux** objet en mode asynchrone.|  
|**adOpenStreamFromRecord**|4|Identifie le contenu de la *Source* le paramètre doit être déjà ouvert [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet. Le comportement par défaut consiste à traiter *Source* comme une URL qui pointe directement vers un nœud dans une arborescence. Le flux par défaut associé à ce nœud est ouvert.|  
|**adOpenStreamUnspecified**|-1|Valeur par défaut. Spécifie l’ouverture du **flux** objet avec les options par défaut.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [Open (méthode) (flux ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)

