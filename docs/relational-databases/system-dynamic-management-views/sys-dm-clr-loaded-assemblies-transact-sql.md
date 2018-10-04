---
title: Sys.dm_clr_loaded_assemblies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_clr_loaded_assemblies
- sys.dm_clr_loaded_assemblies_TSQL
- dm_clr_loaded_assemblies_TSQL
- sys.dm_clr_loaded_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_loaded_assemblies dynamic management view
ms.assetid: 8523d8db-d8a0-4b1f-ae19-6705d633e0a6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c5a65210f7789d49a05785c05df45cda7272040
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715927"
---
# <a name="sysdmclrloadedassemblies-transact-sql"></a>sys.dm_clr_loaded_assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque assembly d'utilisateur géré chargé dans l'espace d'adressage du serveur. Utilisez cette vue pour comprendre et résoudre les problèmes d’intégration du CLR de base de données objets managés qui s’exécutent dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les assemblys sont des fichiers DLL de code managé qui sont utilisés pour définir et déployer des objets de base de données managés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dès lors qu'un utilisateur exécute un de ces objets de base de données managés, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le CLR chargent l'assembly (et ses références) dans lequel l'objet de base de données managé est défini. L'assembly reste chargé dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour augmenter les performances, de sorte que les objets de base de données managés contenus dans l'assembly puissent être appelés ultérieurement, sans avoir à recharger l'assembly. L'assembly n'est pas déchargé tant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne présente pas une mémoire insuffisante. Pour plus d’informations sur les assemblys et intégration du CLR, consultez [CLR hébergé environnement](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md). Pour plus d’informations sur les objets de base de données managés, consultez [création d’objets de base de données avec Common Language Runtime &#40;CLR&#41; intégration](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md).  

  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**Int**|ID de l'assembly chargé. Le **assembly_id** peut être utilisée pour rechercher plus d’informations sur l’assembly dans le [sys.assemblies &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) vue de catalogue. Notez que le [!INCLUDE[tsql](../../includes/tsql-md.md)] [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) catalogue affiche les assemblys dans la base de données actuelle uniquement. Le **sqs.dm_clr_loaded_assemblies** affiche tous les assemblys chargés sur le serveur.|  
|**appdomain_address**|**Int**|Adresse du domaine d’application (**AppDomain**) dans lequel l’assembly est chargé. Tous les assemblys appartenant à un seul utilisateur sont toujours chargés dans le même **AppDomain**. Le **appdomain_address** peut être utilisé pour rechercher plus d’informations sur la **AppDomain** dans le [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md) vue.|  
|**load_time**|**datetime**|Heure à laquelle l'assembly a été chargé. Notez que l’assembly reste chargé tant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est sous pression de mémoire et décharge le **AppDomain**. Vous pouvez surveiller **load_time** à comprendre à quelle fréquence [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fourni avec une mémoire insuffisante et décharge le **AppDomain**.|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Le **dm_clr_loaded_assemblies.appdomain_address** vue a une relation plusieurs-à-un avec **dm_clr_appdomains.appdomain_address**. Le **dm_clr_loaded_assemblies.assembly_id** vue a une relation un-à-plusieurs avec **sys.assemblies.assembly_id**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre comment afficher les détails de tous les assemblys de la base de données active qui sont chargés.  
  
```  
 SELECT a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
FROM sys.dm_clr_loaded_assemblies AS l   
INNER JOIN sys.assemblies AS a  
ON l.assembly_id = a.assembly_id;  
```  
  
 L’exemple suivant montre comment afficher les détails de la **AppDomain** dans lequel un assembly donné est chargé.  
  
```  
SELECT appdomain_id, creation_time, db_id, user_id, state  
FROM sys.dm_clr_appdomains AS a  
WHERE appdomain_address =   
(SELECT appdomain_address   
 FROM sys.dm_clr_loaded_assemblies  
 WHERE assembly_id = 555);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique liées à Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
