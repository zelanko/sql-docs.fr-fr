---
title: sys. resource_usage (Azure SQL Database) | Microsoft Docs
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
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 3be4ff07923759af53b929852d4dbaa4088a77f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67904420"
---
# <a name="sysresource_usage-azure-sql-database"></a>sys.resource_usage (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]
>  Cette fonctionnalité est dans un état d'aperçu. N'établissez pas de dépendance sur l'implémentation spécifique de cette fonctionnalité, car elle est susceptible d'être modifiée ou supprimée dans une future version.  
> 
>  Dans un état d'aperçu, l'équipe d'exploitation de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] peut désactiver et activer la collection de données pour cette vue de gestion dynamique (DMV).  
> 
>  -   Si elle est activée, la DMV retourne les données actives à mesure qu'elles sont agrégées.  
> -   Si elle est désactivée, la DMV retourne les données d'historique, qui peuvent être obsolètes.  
  
 Fournit une synthèse horaire des données d'utilisation des ressources pour les bases de données utilisateur sur le serveur actif. Les données d'historique sont conservées pendant 90 jours.  
  
 Pour chaque base de données utilisateur, contient une ligne pour toutes les heures en continu. Même si la base de données était inactive au cours d'une heure, il y a une ligne, et la valeur de usage_in_seconds de cette base de données sera 0. Les informations sur l'utilisation du stockage et de la référence sont regroupées de la façon appropriée pour l'heure concernée.  
  
|Colonnes|Type de données|Description|  
|-------------|---------------|-----------------|  
|time|**DATETIME**|Heure (UTC) par incréments d'heures.|  
|database_name|**nvarchar**|Nom de la base de données utilisateur.|  
|sku|**nvarchar**|Nom de la SKU. Les valeurs possibles sont les suivantes :<br /><br /> Web<br /><br /> Business<br /><br /> De base<br /><br /> standard<br /><br /> Premium|  
|usage_in_seconds|**int**|Somme du temps processeur utilisé dans l'heure.<br /><br /> Remarque : cette colonne est déconseillée pour v11 et ne s’applique pas à v12. **La valeur est toujours définie sur 0.**|  
|storage_in_megabytes|**sépar**|Taille de stockage maximale pour l'heure, y compris les données de la base de données, index, procédures stockées et métadonnées.|  
  
## <a name="permissions"></a>Autorisations  
 Cette vue est disponible pour tous les rôles d’utilisateur disposant d’autorisations pour se connecter à la base de données **Master** virtuelle.  
  
  
