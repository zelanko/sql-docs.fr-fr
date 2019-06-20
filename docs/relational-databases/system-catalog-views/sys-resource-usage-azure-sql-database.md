---
title: Sys.resource_usage (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_usage_TSQL
- resource_usage
- sys.resource_usage
- resource_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- resource_usage
- sys.resource_usage
ms.assetid: b90147a3-fd8e-408e-961d-5c7000e068ad
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9b0e16279615bf102c916793439d440211939839
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63025407"
---
# <a name="sysresourceusage-azure-sql-database"></a>sys.resource_usage (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]
>  Cette fonctionnalité est dans un état d'aperçu. N'établissez pas de dépendance sur l'implémentation spécifique de cette fonctionnalité, car elle est susceptible d'être modifiée ou supprimée dans une future version.  
> 
>  Dans un état d'aperçu, l'équipe d'exploitation de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] peut désactiver et activer la collection de données pour cette vue de gestion dynamique (DMV).  
> 
>  -   Si elle est activée, la DMV retourne les données actives à mesure qu'elles sont agrégées.  
> -   Si elle est désactivée, la DMV retourne les données d'historique, qui peuvent être obsolètes.  
  
 Fournit une synthèse horaire des données d'utilisation des ressources pour les bases de données utilisateur sur le serveur actif. Les données historiques sont conservées pendant 90 jours.  
  
 Pour chaque base de données utilisateur, contient une ligne pour toutes les heures en continu. Même si la base de données était inactive au cours d'une heure, il y a une ligne, et la valeur de usage_in_seconds de cette base de données sera 0. Les informations sur l'utilisation du stockage et de la référence sont regroupées de la façon appropriée pour l'heure concernée.  
  
|Colonnes|Type de données|Description|  
|-------------|---------------|-----------------|  
|time|**datetime**|Heure (UTC) par incréments d'heures.|  
|database_name|**nvarchar**|Nom de la base de données utilisateur.|  
|sku|**nvarchar**|Nom de la SKU. Les valeurs possibles sont les suivantes :<br /><br /> Web<br /><br /> Business<br /><br /> Simple<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**Int**|Somme du temps processeur utilisé dans l'heure.<br /><br /> Remarque : Cette colonne est déconseillée pour V11 et V12 ne concerne pas. **Valeur est toujours définie sur 0.**|  
|storage_in_megabytes|**decimal**|Taille de stockage maximale pour l'heure, y compris les données de la base de données, index, procédures stockées et métadonnées.|  
  
## <a name="permissions"></a>Autorisations  
 Cette vue est disponible pour tous les rôles d’utilisateur avec des autorisations pour se connecter à virtuel **master** base de données.  
  
  
