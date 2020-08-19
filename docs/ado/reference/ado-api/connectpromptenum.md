---
description: ConnectPromptEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ad8fe77bb3472931d3b16d5849b047001922c96
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444411"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Spécifie si une boîte de dialogue doit être affichée pour demander des paramètres manquants lors de l’ouverture d’une connexion à une source de données.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|Les invites s’affichent toujours.|  
|**adPromptComplete**|2|Demande si des informations supplémentaires sont requises.|  
|**adPromptCompleteRequired**|3|Demande si des informations supplémentaires sont requises, mais que les paramètres facultatifs ne sont pas autorisés.|  
|**adPromptNever**|4|Ne jamais demander.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>S'applique à  
 [Prompt, propriété dynamique (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
