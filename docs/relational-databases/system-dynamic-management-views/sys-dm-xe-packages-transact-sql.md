---
title: Sys.dm_xe_packages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_packages_TSQL
- sys.dm_xe_packages_TSQL
- dm_xe_packages
- sys.dm_xe_packages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_packages dynamic management view
- extended events [SQL Server], views
ms.assetid: 2e5ecbe9-3ea8-45e6-a161-e31671a03e1d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 065625fdaca015de9c445e6e6f0e1ad0013f38e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090258"
---
# <a name="sysdmxepackages-transact-sql"></a>sys.dm_xe_packages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie tous les packages enregistrés avec le moteur des événements étendus.  
  
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar (256)**|Le nom du package. La description est exposée à partir du package lui-même. N'accepte pas la valeur NULL.|  
|GUID|**uniqueidentifier**|GUID qui identifie le package. N'accepte pas la valeur NULL.|  
|description|**nvarchar(3072)**|La description du package. descriptionis définie par l’auteur du package et n’est pas nullable.|  
|Fonctionnalités|**Int**|Bitmap décrivant les fonctionnalités de ce package. Autorise la valeur NULL.|  
|capabilities_desc|**nvarchar (256)**|Liste de toutes les fonctionnalités disponibles pour ce package. Autorise la valeur NULL.|  
|module_guid|**nvarchar(60)**|GUID du module qui expose ce package. N'accepte pas la valeur NULL.|  
|module_address|**varbinary(8)**|Adresse de base où le module contenant le package est chargé. Un module peut exposer plusieurs packages. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Les packages enregistrés avec le moteur d'événements étendus exposent des événements, les actions qui peuvent être exécutées au moment du déclenchement des événements, et des cibles pour le traitement synchrone et asynchrone de données d'événement.  
  
 Ces packages peuvent être chargés dynamiquement dans un espace d'adressage de processus. Lorsque le package est chargé, il enregistre tous les objets qu'il expose avec le moteur d'événements étendus.  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
||||  
|-|-|-|  
|From|Pour|Relation|  
|sys.dm_xe_packages.module_address|sys.dm_os_loaded_modules.base_address|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

