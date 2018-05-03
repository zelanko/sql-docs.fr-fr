---
title: ConnectPromptEnum | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e66c3cea7f4eefa711aa4250d4474b10cf68d65
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Spécifie si une boîte de dialogue doit être affichée pour demander les paramètres manquants lors de l’ouverture d’une connexion à une source de données.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|Toujours demander.|  
|**adPromptComplete**|2|Vous demande si plus d’informations est nécessaire.|  
|**adPromptCompleteRequired**|3|Vous demande si plus d’informations est requis mais les paramètres optionnels ne sont pas autorisés.|  
|**adPromptNever**|4|Ne jamais demander.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>S'applique à  
 [Prompt, propriété dynamique (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
