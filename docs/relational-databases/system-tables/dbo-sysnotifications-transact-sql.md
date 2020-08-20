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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a55ba4b149466f127ee7e4d96d0df5677004bf56
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480824"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contient une ligne pour chaque notification.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID de l'alerte.|  
|**operator_id**|**int**|ID de l'opérateur à qui la notification doit être envoyée.|  
|**notification_method**|**tinyint**|Méthode de notification :<br /><br /> **1** = courrier électronique<br /><br /> **2** = radiomessagerie<br /><br /> **4**  =  **envoi** de la<br /><br /> **7** = tous|  
  
  
