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
ms.openlocfilehash: 2c9032dfdb3394e582541f60afce7b930751a5c0
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777778"
---
# <a name="actionenum"></a>ActionEnum
Spécifie le type d’action à effectuer lorsque l’opération [SetPermissions](./setpermissions-method-adox.md) est appelée.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAccessDeny**|3|Les autorisations spécifiées sont refusées au groupe ou à l’utilisateur.|  
|**adAccessGrant**|1|Le groupe ou l’utilisateur aura au moins les autorisations demandées.|  
|**adAccessRevoke**|4|Tous les droits d’accès explicites du groupe ou de l’utilisateur seront révoqués.|  
|**adAccessSet**|2|Le groupe ou l’utilisateur aura exactement les autorisations demandées.|