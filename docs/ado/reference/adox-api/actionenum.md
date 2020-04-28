---
title: ActionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActionEnum
helpviewer_keywords:
- ActionEnum enumeration [ADOX]
ms.assetid: f948febd-c885-4621-823b-421e116fec4e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fad40c6daed6fd86f93da3f658af6a21c33ca762
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928623"
---
# <a name="actionenum"></a>ActionEnum
Spécifie le type d’action à effectuer lorsque l’opération [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) est appelée.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAccessDeny**|3|Les autorisations spécifiées sont refusées au groupe ou à l’utilisateur.|  
|**adAccessGrant**|1|Le groupe ou l’utilisateur aura au moins les autorisations demandées.|  
|**adAccessRevoke**|4|Tous les droits d’accès explicites du groupe ou de l’utilisateur seront révoqués.|  
|**adAccessSet**|2|Le groupe ou l’utilisateur aura exactement les autorisations demandées.|
