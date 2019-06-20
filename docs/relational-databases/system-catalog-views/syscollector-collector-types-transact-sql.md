---
title: syscollector_collector_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_collector_types
- syscollector_collector_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collector_types view
ms.assetid: d5cd30bb-89fd-4814-a7e8-9074f043f90f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41ae978e31db70f0cc49469d5ec14ae6f075ab7e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62760236"
---
# <a name="syscollectorcollectortypes-transact-sql"></a>syscollector_collector_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur un type de collecteur pour un élément de collecte.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**collector_type_uid**|**uniqueidentifer**|GUID pour un type de collecte. N'accepte pas la valeur NULL.|  
|**nom**|**sysname**|Nom du type de collecte. N'accepte pas la valeur NULL.|  
|**parameter_schema**|**xml**|Schéma XML qui décrit l'aspect de la configuration pour le type de collecteur spécifié. Ce schéma XML est utilisé pour valider la configuration XML réelle associée à l'instance d'un élément de collecte particulier. Autorise la valeur NULL.|  
|**parameter_formatter**|**xml**|Détermine le modèle à utiliser pour transformer le XML utilisé dans la page de propriétés du jeu d'éléments de collecte. Autorise la valeur NULL.|  
|**collection_package_id**|**uniqueidentifer**|GUID pour un package de collecte. N'accepte pas la valeur NULL.|  
|**collection_package_path**|**nvarchar(4000)**|Fournit le chemin d'accès au package de collecte. Autorise la valeur NULL.|  
|**collection_package_name**|**sysname**|Nom du package de collecte. N'accepte pas la valeur NULL.|  
|**upload_package_id**|**uniqueidentifer**|GUID pour le package à télécharger. N'accepte pas la valeur NULL.|  
|**upload_package_path**|**nvarchar(4000)**|Fournit le chemin d'accès au package à télécharger. Autorise la valeur NULL.|  
|**upload_package_name**|**sysname**|Nom du package à télécharger. N'accepte pas la valeur NULL.|  
|**is_system**|**bit**|Activé (1) ou désactivé (0) pour indiquer si le type de collecteur a été livré avec le collecteur de données ou s’il a été ajouté ultérieurement par le **dc_admin**. Il peut s'agir d'un type personnalisé développé en interne ou par un tiers. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation SELECT pour **dc_operator**, **dc_proxy**.  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Mise à jour **collection_type_uid** nom de colonne à **collector_type_uid**.|  
|Correction de la description pour le **parameter_schema** colonne afin d’indiquer que la valeur est nullable.|  
|Ajouté le **parameter_formatter** colonne.|  
|Correction du type de données pour le **collection_package_path** colonne et la mise à jour la description pour indiquer que la valeur null.|  
|Correction du type de données pour le **upload_package_path** colonne et la mise à jour la description pour indiquer que la valeur null.|  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Vues du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
