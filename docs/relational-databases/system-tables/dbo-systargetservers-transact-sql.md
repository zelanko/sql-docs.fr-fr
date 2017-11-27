---
title: dbo.systargetservers (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs: TSQL
helpviewer_keywords: systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8d7dcb3e9abf5e653c936aac5684c21d30afd44
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enregistrements dont les serveurs cibles font actuellement partie de la liste du domaine d'exploitation multiserveurs.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID du serveur.|  
|**nom_serveur**|**sysname**|Nom du serveur.|  
|**emplacement**|**nvarchar(200)**|Emplacement du serveur cible spécifié.|  
|**TIME_ZONE_ADJUSTMENT**|**int**|Intervalle d'ajustement, en heures, par rapport à l'heure de Greenwich (GMT).|  
|**enlist_date**|**datetime**|Date et heure d'enregistrement du serveur cible spécifié.|  
|**last_poll_date**|**datetime**|Date et heure auxquelles le serveur cible spécifié a interrogé pour la dernière fois de multiserver **sysdownloadlist** (table système) pour les travaux à exécuter.|  
|**status**|**int**|État du serveur cible :<br /><br /> **1** = Normal<br /><br /> **2** = en attente de resynchronisation<br /><br /> **4** = hors-connexion suspectée|  
|**local_time_at_last_poll**|**datetime**|Date et heure auxquelles le serveur cible a été interrogé pour la dernière fois pour un travail.|  
|**enlisted_by_nt_user**|**nvarchar (100)**|Nom d’utilisateur de la personne exécutant **sp_msx_enlist** sur le serveur cible.|  
|**poll_internal**|**int**|Nombre de secondes devant s'écouler avant que le serveur cible n'interroge le serveur maître pour de nouvelles instructions de téléchargement.|  
  
  
