---
title: Sys.database_connection_stats (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.database_connection_stats
- database_connection_stats
- database_connection_stats_TSQL
- sys.database_connection_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_connection_stats
- database_connection_stats
ms.assetid: 5c8cece0-63b0-4dee-8db7-6b43d94027ec
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9d9e6f23d9e73295f34f23777c76253d27671ed8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012360"
---
# <a name="sysdatabaseconnectionstats-azure-sql-database"></a>sys.database_connection_stats (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Contient des statistiques pour [!INCLUDE[ssSDS](../../includes/sssds-md.md)] base de données **connectivité** événements, qui fournissent une vue d’ensemble de réussites de connexion de base de données et d’échecs. Pour plus d’informations sur les événements de connectivité, consultez Types d’événements dans [sys.event_log &#40;base de données SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md).  
  
|Statistique|Type|Description|  
|---------------|----------|-----------------|  
|**database_name**|**sysname**|Nom de la base de données.|  
|**start_time**|**datetime2**|Date et heure UTC indiquant le début de l'intervalle d'agrégation. L'heure est toujours un multiple de 5 minutes. Exemple :<br /><br /> '2011-09-28 16:00:00'<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|Date et heure UTC indiquant la fin de l'intervalle d'agrégation. **End_time** est toujours exactement à cinq minutes plus tard correspondant **start_time** dans la même ligne.|  
|**success_count**|**Int**|Nombre de connexions réussies.|  
|**total_failure_count**|**Int**|Nombre total d'échecs de connexion. C’est la somme de **connection_failure_count**, **terminated_connection_count**, et **throttled_connection_count**et n’inclut pas les événements de blocage.|  
|**connection_failure_count**|**Int**|Nombre d'échecs de connexion.|  
|**terminated_connection_count**|**Int**|**_Applicable uniquement pour [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] v11._**<br /><br /> Nombre de connexions terminées.|  
|**throttled_connection_count**|**Int**|**_Applicable uniquement pour [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] v11._**<br /><br /> Nombre de connexions limitées.|  
  
## <a name="remarks"></a>Notes  
  
### <a name="event-aggregation"></a>Agrégation d'événements

 Les informations relatives aux événements de cette vue sont collectées et agrégées par intervalles de 5 minutes. Les colonnes de nombre représentent le nombre de fois qu'un événement particulier de connectivité s'est produit pour une base de données spécifique dans un intervalle de temps donné.  
  
 Par exemple, si un utilisateur ne parvient pas à se connecter à la base de données Database1 sept fois entre 11h00 et 11h05 le 5/2/2012 (UTC), ces informations sont disponibles dans une ligne de cette vue :  
  
|**database_name**|**start_time**|**end_time**|**success_count**|**total_failure_count**|**connection_failure_count**|**terminated_connection_count**|**throttled_connection_count**|  
|------------------------|---------------------|-------------------|------------------------|-------------------------------|------------------------------------|---------------------------------------|--------------------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`0`|`7`|`7`|`0`|`0`|  
  
### <a name="interval-starttime-and-endtime"></a>Heure de début (start_time) et heure de fin (end_time) de l'intervalle

 Un événement est inclus dans un intervalle d’agrégation lorsque l’événement se produit *sur* ou _après_**start_time** et _avant_  **end_time** pour cet intervalle. Par exemple, un événement se produisant exactement à `2012-10-30 19:25:00.0000000` est inclus uniquement dans le deuxième intervalle indiqué ci-dessous :  
  
```  
  
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```  
  
### <a name="data-updates"></a>Mises à jour des données

 Les données de cette vue sont cumulées au fil du temps. Généralement, les données sont cumulées pendant une heure à compter du début de l'intervalle d'agrégation, mais cela peut prendre jusqu'à 24 heures avant que toutes les données apparaissent dans la vue. Pendant ce temps, les informations d'une seule ligne peuvent être mises à jour périodiquement.  
  
### <a name="data-retention"></a>Rétention des données

 Les données dans cette vue sont conservées pendant un maximum de 30 jours, et même moins encore selon le nombre de bases de données et le nombre d’événements uniques que génère chaque base de données. Pour conserver ces informations plus longtemps, copiez les données dans une base de données distincte. Une fois que vous avez effectué une copie initiale de la vue, les lignes de la vue peuvent être mises à jour au fur et à mesure que les données sont cumulées. Pour tenir à jour votre copie des données, effectuez périodiquement une analyse des lignes de la table pour détecter une augmentation du nombre d'événements dans les lignes existantes et pour identifier les nouvelles lignes (vous pouvez identifier les lignes qui sont uniques à l'aide des heures de début et de fin), puis mettez à jour votre copie des données en fonction de ces modifications.  
  
### <a name="errors-not-included"></a>Erreurs non incluses.

 Cette vue peut ne pas inclure toutes les informations de connexion et d'erreur :  
  
- Cette vue n’inclut pas toutes [!INCLUDE[ssSDS](../../includes/sssds-md.md)] erreurs peuvent se produire, uniquement celles spécifiées dans les Types d’événements dans la base de données [sys.event_log &#40;base de données SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md).  
  
- S’il existe une défaillance d’ordinateur dans le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] centre de données, une petite quantité de données est peut-être manquante dans la table d’événements.  
  
- Si une adresse IP a été bloquée par DoSGuard, les événements de tentative de connexion à partir de cette adresse IP ne peuvent pas être collectés et n'apparaitront pas dans cette vue.  
  
## <a name="permissions"></a>Autorisations

 Les utilisateurs autorisés à accéder à la **master** base de données ont un accès en lecture seule à cette vue.  
  
## <a name="example"></a>Exemple

 L’exemple suivant montre une requête de **sys.database_connection_stats** pour retourner un résumé des connexions de base de données qui se sont produites entre midi le 25/9/2011 et MIDI le 28/9/2011 (UTC). Par défaut, les résultats de requête sont triés par **start_time** (ordre croissant).  
  
```sql
SELECT *  
FROM sys.database_connection_stats
WHERE start_time>='2011-09-25:12:00:00' and end_time<='2011-09-28 12:00:00';  
```  

## <a name="see-also"></a>Voir aussi

 [Résolution des problèmes de Windows Azure SQL Database](https://msdn.microsoft.com/library/windowsazure/ee730906.aspx)  
  
  
