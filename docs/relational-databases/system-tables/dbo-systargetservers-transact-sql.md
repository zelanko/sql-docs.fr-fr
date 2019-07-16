---
title: dbo.systargetservers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c6304b108d75d6fe9ba00ccccdae322bf7cedde
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68095840"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enregistrements dont les serveurs cibles font actuellement partie de la liste du domaine d'exploitation multiserveurs.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**Int**|ID de serveur.|  
|**server_name**|**sysname**|Nom du serveur.|  
|**location**|**nvarchar(200)**|Emplacement du serveur cible spécifié.|  
|**time_zone_adjustment**|**Int**|Intervalle d'ajustement, en heures, par rapport à l'heure de Greenwich (GMT).|  
|**enlist_date**|**datetime**|Date et heure d'enregistrement du serveur cible spécifié.|  
|**last_poll_date**|**datetime**|Date et heure auxquelles le serveur cible spécifié a interrogé pour la dernière fois le multiserveurs **sysdownloadlist** (table système) pour les travaux à exécuter.|  
|**status**|**Int**|État du serveur cible :<br /><br /> **1** = Normal<br /><br /> **2** = en attente de resynchronisation<br /><br /> **4** = hors-connexion suspectée|  
|**local_time_at_last_poll**|**datetime**|Date et heure auxquelles le serveur cible a été interrogé pour la dernière fois pour un travail.|  
|**enlisted_by_nt_user**|**nvarchar(100)**|Nom d’utilisateur de la personne qui exécute **sp_msx_enlist** sur le serveur cible.|  
|**poll_internal**|**Int**|Nombre de secondes devant s'écouler avant que le serveur cible n'interroge le serveur maître pour de nouvelles instructions de téléchargement.|  
  
  
