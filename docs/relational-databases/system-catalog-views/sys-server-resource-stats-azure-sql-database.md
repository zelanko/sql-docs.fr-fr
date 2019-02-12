---
title: Sys.server_resource_stats (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.service: sql-database
ms.reviewer: carlrab, edmaca
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: b8a5aaa7d0aecd992905e0eaf53ef362f24b1485
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009651"
---
# <a name="sysserverresourcestats-azure-sql-database"></a>Sys.server_resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Retourne les données de stockage, d’e/s et l’utilisation du processeur pour Azure SQL Managed Instance. Les données sont collectées et agrégées dans des intervalles de cinq minutes. Il existe une ligne pour toutes les 15 secondes reporting. Les données retournées incluent l’utilisation du processeur, la taille de stockage, l’utilisation d’e/s et instance gérée référence (SKU). Les données historiques sont conservées pendant environ 14 jours.

Le **sys.server_resource_stats** vue a des définitions différentes selon la version de l’instance gérée de SQL Azure qui est associé à la base de données. Tenez compte de ces différences et des modifications requises par votre application lors de la mise à niveau vers une nouvelle version de serveur.
 
  
 Le tableau suivant décrit les colonnes disponibles dans un serveur v12 :  
  
|Colonnes|Type de données|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime2**|Heure UTC indiquant le début de l’intervalle de création de rapports de quinze secondes|  
|end_time|**datetime**|Heure UTC indiquant la fin de l’intervalle de création de rapports de quinze secondes|
|resource_type|Nvarchar(128)|Type de la ressource pour laquelle les métriques sont fournies|
|resource_name|nvarchar(128)|Nom de la ressource.|
|sku|nvarchar(128)|Managed Instance niveau de Service de l’Instance. Les valeurs possibles sont les suivantes : <br><ul><li>Usage général</li></ul><ul><li>Critique pour l’entreprise</li></ul>|
|hardware_generation|nvarchar(128)|Identificateur de génération de matériel : comme Gen 4 ou Gen 5|
|virtual_core_count|INT|Représente le nombre de cœurs virtuels par instance (8, 16 ou 24 en version préliminaire publique)|
|avg_cpu_percent|decimal(5,2)|Utilisation de calcul moyenne en pourcentage de la limite du niveau de service Managed Instance utilisée par l’instance. Il est calculé comme la somme du temps processeur de tous les pools de ressources pour toutes les bases de données dans l’instance et divisé par le temps processeur disponible pour ce niveau dans l’intervalle spécifié.|
|reserved_storage_mb|BIGINT|Réservé de stockage par instance (quantité de stockage de l’espace que le client acheté pour l’instance managée)|
|storage_space_used_mb|decimal(18,2)|Stockage utilisé par les fichiers de toutes les bases instance gérée (y compris les bases de données utilisateur et système)|
|io_request|BIGINT|Nombre total de d’opérations d’e/s physiques au sein de l’intervalle|
|io_bytes_read|BIGINT|Nombre d’octets physiques lus dans l’intervalle|
|io_bytes_written|BIGINT|Nombre d’octets physiques écrits dans l’intervalle|

 
> [!TIP]  
>  Pour plus d’informations sur ces limites et les niveaux de service, consultez les rubriques [les niveaux de service de Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tier).  
    
## <a name="permissions"></a>Autorisations  
 Cette vue est disponible pour tous les rôles d’utilisateur avec des autorisations pour se connecter à la **master** base de données.  
  
## <a name="remarks"></a>Notes  
 Les données retournées par **sys.server_resource_stats** sont exprimées en tant que le total utilisé en octets ou mégaoctets (indiqués dans les noms de colonne) autre qu’avg_cpu, exprimé sous la forme d’un pourcentage de la valeur maximale autorisée des limites pour le service niveau/niveau de performances qui vous sont en cours d’exécution.  
 
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne toutes les bases de données dont la moyenne s'établit à au moins 80 % de l'utilisation du calcul au cours de la dernière semaine.  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT resource_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.server_resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY resource_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>Voir aussi  
 [Gérés des niveaux de service d’Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tier)
