---
title: ConnectPromptEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ConnectPromptEnum
helpviewer_keywords: ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 89c339b294a3afc968a6a9f5307d3a06995a7454
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Spécifie si une boîte de dialogue doit être affichée pour demander les paramètres manquants lors de l’ouverture d’une connexion à une source de données.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPromptAlways**| 1|Toujours demander.|  
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
