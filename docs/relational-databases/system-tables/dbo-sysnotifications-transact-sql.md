---
title: dbo. sysnotifications précise (Transact-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef7a5456f0bae470bcbf1f12f37843aa6c311d78
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67984922"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque notification.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID de l'alerte.|  
|**operator_id**|**int**|ID de l'opérateur à qui la notification doit être envoyée.|  
|**notification_method**|**tinyint**|Méthode de notification :<br /><br /> **1** = courrier électronique<br /><br /> **2** = radiomessagerie<br /><br /> **4** = **NetSend**<br /><br /> **7** = tous|  
  
  
