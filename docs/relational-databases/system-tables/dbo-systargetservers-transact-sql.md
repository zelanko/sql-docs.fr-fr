---
description: dbo.systargetservers (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6ecf738591688ba3ad25c58f6b77dabec5df73b2
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538313"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
  
