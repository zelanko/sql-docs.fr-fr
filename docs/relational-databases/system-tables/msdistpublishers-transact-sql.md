---
title: MSdistpublishers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c70ea03659fe65b594555dd6bbbba7a650558e88
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832328"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  La table **MSdistpublishers** contient une ligne pour chaque serveur de publication distant pris en charge par le serveur de distribution local. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom du serveur de distribution du serveur de publication.|  
|**bd_distribution**|**sysname**|Nom de la base de données de distribution.|  
|**working_directory**|**nvarchar(255)**|Nom du répertoire de travail utilisé pour stocker les fichiers de données et de schéma de la publication.|  
|**security_mode**|**int**|Mode de sécurité implémenté sur le serveur de distribution :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification.<br /><br /> **1** = authentification Windows.|  
|**connexion**|**sysname**|ID de connexion pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**mot de passe**|**nvarchar (524)**|Mot de passe (chiffré) pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**active**|**bit**|Indique si le serveur de distribution local est utilisé par le serveur de publication distant.|  
|**trusted**|**bit**|Indique si le serveur de publication distant utilise le même mot de passe que le serveur de distribution local :<br /><br /> **0** = un mot de passe est requis sur le serveur de publication distant pour se connecter au serveur de distribution.<br /><br /> **1** = aucun mot de passe n’est nécessaire.|  
|**third_party**|**bit**|Spécifie si le serveur de publication est une installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.** 1** = source de données hétérogènes.|  
|**publisher_type**|**sysname**|Type du serveur de publication :<br /><br /> **MSSQLSERVER**  =  MSSQLSERVER [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publication.<br /><br /> **Oracle** = serveur de publication Oracle standard.<br /><br /> **Passerelle Oracle** = serveur de publication de passerelle Oracle.|  
|**storage_connection_string**|**nvarchar (779)**|Valeur de Azure SQL Database chaîne de connexion de stockage.|  

  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
