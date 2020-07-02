---
title: dbo.sysTargetServers (Transact-SQL) | Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 063744d15d0f4ad6d7ce8bd4895d254aaecd2931
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750241"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Enregistrements dont les serveurs cibles font actuellement partie de la liste du domaine d'exploitation multiserveurs.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID du serveur.|  
|**server_name**|**sysname**|Nom du serveur.|  
|**location**|**nvarchar(200)**|Emplacement du serveur cible spécifié.|  
|**time_zone_adjustment**|**int**|Intervalle d'ajustement, en heures, par rapport à l'heure de Greenwich (GMT).|  
|**enlist_date**|**datetime**|Date et heure d'enregistrement du serveur cible spécifié.|  
|**last_poll_date**|**datetime**|Date et heure auxquelles le serveur cible spécifié a interrogé pour la dernière fois la table système **sysdownloadlist** MultiServer pour les travaux à exécuter.|  
|**statut**|**int**|État du serveur cible :<br /><br /> **1** = normal<br /><br /> **2** = resynchronisation en attente<br /><br /> **4** = en mode hors connexion suspect|  
|**local_time_at_last_poll**|**datetime**|Date et heure auxquelles le serveur cible a été interrogé pour la dernière fois pour un travail.|  
|**enlisted_by_nt_user**|**nvarchar(100**|Nom d’utilisateur de la personne qui exécute **sp_msx_enlist** sur le serveur cible.|  
|**poll_internal**|**int**|Nombre de secondes devant s'écouler avant que le serveur cible n'interroge le serveur maître pour de nouvelles instructions de téléchargement.|  
  
  
