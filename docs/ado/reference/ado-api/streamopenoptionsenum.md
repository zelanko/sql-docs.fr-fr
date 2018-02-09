---
title: StreamOpenOptionsEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e234d22e68d90819d73702542f7d3763ddd2f8c3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
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
 [Open, méthode (objet Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
