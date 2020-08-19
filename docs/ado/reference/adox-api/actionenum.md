---
description: ActionEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 78c931cdbc37d73942baa72b41d8c8071f107c8d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440661"
---
# <a name="actionenum"></a>ActionEnum
Spécifie le type d’action à effectuer lorsque l’opération [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) est appelée.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAccessDeny**|3|Les autorisations spécifiées sont refusées au groupe ou à l’utilisateur.|  
|**adAccessGrant**|1|Le groupe ou l’utilisateur aura au moins les autorisations demandées.|  
|**adAccessRevoke**|4|Tous les droits d’accès explicites du groupe ou de l’utilisateur seront révoqués.|  
|**adAccessSet**|2|Le groupe ou l’utilisateur aura exactement les autorisations demandées.|
