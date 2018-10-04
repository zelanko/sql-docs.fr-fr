---
title: Sys.dm_server_registry (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_registry_TSQL
- sys.dm_server_registry
- dm_server_registry
- sys.dm_server_registry_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_registry dynamic management view
ms.assetid: 9b3e0c74-2e99-4996-a383-104d51831e97
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e4e0b1069977c14216952e537d4bd12b28190529
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788617"
---
# <a name="sysdmserverregistry-transact-sql"></a>sys.dm_server_registry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les informations relatives à la configuration et à l'installation qui sont stockées dans le Registre de Windows pour l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Retourne une ligne par clé de Registre. Utilisez cette vue de gestion dynamique pour retourner des informations telles que les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles sur l'ordinateur hôte ou les valeurs de configuration réseau pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|registry_key|**nvarchar (256)**|Nom de la clé de Registre. Autorise la valeur NULL.|  
|value_name|**nvarchar (256)**|Nom de la valeur de la clé. Ceci est l’élément indiqué dans le **nom** colonne de l’Éditeur du Registre. Autorise la valeur NULL.|  
|value_data|**sql_variant**|Valeur des données de la clé. Ceci est la valeur affichée dans le **données** colonne de l’Éditeur du Registre pour une entrée donnée. Autorise la valeur NULL.|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-display-the-sql-server-services"></a>A. Affichage des services SQL Server  
 L'exemple suivant retourne les valeurs de clé de Registre pour les services SQL Server et SQL Server Agent pour l'instance actuelle de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%ControlSet%';  
```  
  
### <a name="b-display-the-sql-server-agent-registry-key-values"></a>B. Affichage des valeurs de clés de Registre de Le SQL Server Agent  
 L'exemple suivant retourne les valeurs de clés de Registre de Le SQL Server Agent pour l'instance actuelle de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SQLAgent%';  
```  
  
### <a name="c-display-the-current-version-of-the-instance-of-sql-server"></a>C. Affichage de la version actuelle de l'instance de SQL Server  
 L'exemple suivant retourne la version de l'instance actuelle de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key = N'CurrentVersion';  
```  
  
### <a name="d-display-the-parameters-passed-to-the-instance-of-sql-server-during-startup"></a>D. Affichage des paramètres passés à l'instance de SQL Server pendant le démarrage  
 L'exemple suivant retourne les paramètres passés à l'instance de SQL Server pendant le démarrage.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%Parameters';  
```  
  
### <a name="e-return-network-configuration-information-for-the-instance-of-sql-server"></a>E. Retour des informations de configuration réseau pour l'instance de SQL Server  
 L'exemple suivant retourne les valeurs de configuration réseau pour l'instance actuelle de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SuperSocketNetLib%';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_server_services &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md)  
  
  
