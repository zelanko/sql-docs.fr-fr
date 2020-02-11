---
title: ConnectPromptEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afd5d9ca0de6b8d2ffba75f862e6ca0afb594848
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919446"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Spécifie si une boîte de dialogue doit être affichée pour demander des paramètres manquants lors de l’ouverture d’une connexion à une source de données.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|Les invites s’affichent toujours.|  
|**adPromptComplete**|2|Demande si des informations supplémentaires sont requises.|  
|**adPromptCompleteRequired**|3|Demande si des informations supplémentaires sont requises, mais que les paramètres facultatifs ne sont pas autorisés.|  
|**adPromptNever**|4|Ne jamais demander.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>S'applique à  
 [Prompt, propriété dynamique (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
