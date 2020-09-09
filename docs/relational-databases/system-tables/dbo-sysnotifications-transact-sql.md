---
description: dbo.sysnotifications (Transact-SQL)
title: Notifications de dbo.sys(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysnotifications_TSQL
- sysnotifications
- sysnotifications_TSQL
- dbo.sysnotifications
dev_langs:
- TSQL
helpviewer_keywords:
- sysnotifications system table
ms.assetid: c5150d18-e8b7-48a7-ada7-77c583af6e41
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8bcfd6b5b52a4f091337d55681be149ccd3f7900
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540352"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contient une ligne pour chaque notification.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID de l'alerte.|  
|**operator_id**|**int**|ID de l'opérateur à qui la notification doit être envoyée.|  
|**notification_method**|**tinyint**|Méthode de notification :<br /><br /> **1** = courrier électronique<br /><br /> **2** = radiomessagerie<br /><br /> **4**  =  **envoi** de la<br /><br /> **7** = tous|  
  
  
