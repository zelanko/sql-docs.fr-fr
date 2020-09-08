---
description: MSsubscriber_info (Transact-SQL)
title: MSsubscriber_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d949fe0234cad850a1080b727f0917df6e6a24af
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89523804"
---
# <a name="mssubscriber_info-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La table **MSsubscriber_info** contient une ligne pour chaque paire serveur de publication/abonné faisant l’objet d’un push d’abonnements à partir du serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
 **Remarque** Cette table système est déconseillée et est en cours de maintenance pour prendre en charge les versions antérieures de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nom du serveur de publication.|  
|**côté**|**sysname**|Nom de l'Abonné.|  
|**type**|**tinyint**|Type d'abonné :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonné.<br /><br /> **1** = source de données ODBC.|  
|**connexion**|**sysname**|Connexion pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Stocké sous forme chiffrée si l'Abonné est ajouté à l'aide du mode d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**mot de passe**|**nvarchar (524)**|Mot de passe pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Stocké sous forme chiffrée si l'Abonné est ajouté à l'aide du mode d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**description**|**nvarchar(255)**|Description de l'abonné.|  
|**security_mode**|**int**|Mode de sécurité implémenté :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] authentification Windows.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
