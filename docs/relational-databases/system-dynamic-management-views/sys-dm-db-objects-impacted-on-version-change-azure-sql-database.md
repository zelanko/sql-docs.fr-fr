---
title: Sys.dm_db_objects_impacted_on_version_change (base de données Azure SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_objects_impacted_on_version_change_TSQL
- dm_db_objects_impacted_on_version_change
- dm_db_objects_impacted_on_version_change_TSQL
- sys.dm_db_objects_impacted_on_version_change
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_objects_impacted_on_version_change
- sys.dm_db_objects_impacted_on_version_change
ms.assetid: b94af834-c4f6-4a27-80a6-e8e71fa8793a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 11445fefd94925f32e40173491f27b8ea0837218
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645357"
---
# <a name="sysdmdbobjectsimpactedonversionchange-azure-sql-database"></a>sys.dm_db_objects_impacted_on_version_change (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Cette vue système dont l'étendue est la base de données est conçue pour fournir un système d'avertissement anticipé pour déterminer les objets qui seront affectés par une mise à niveau de version majeure dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Utilisez cette vue avant ou après la mise à niveau pour obtenir une énumération complète des objets affectés. Vous devez interroger cette vue dans chaque base de données pour obtenir le nombre total sur le serveur.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|class|**int** pas NULL|Classe de l'objet qui sera affecté :<br /><br /> **1** = contrainte<br /><br /> **7** = index et segments|  
|class_desc|**nvarchar (60)** pas NULL|Description de la classe :<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **INDEX**|  
|major_id|**int** pas NULL|ID d'objet de la contrainte, ou ID d'objet de la table contenant l'index ou le segment de mémoire.|  
|minor_id|**int** NULL|**NULL** pour les contraintes<br /><br /> Index_id pour les index et les segments|  
|dependency|**nvarchar (60)** pas NULL|Description de la dépendance qui provoque l'impact sur une contrainte ou un index. La valeur est également utilisée pour les avertissements générés pendant la mise à niveau.<br /><br /> Exemples :<br /><br /> **espace** (pour intrinsèque)<br /><br /> **géométrie** (pour système UDT)<br /><br /> **Geography::Parse** (pour système de méthode UDT)|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation VIEW DATABASE STATE.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une requête sur **sys.dm_db_objects_impacted_on_version_change** pour rechercher les objets affectés par une mise à niveau vers la prochaine version majeure de serveur  
  
```  
SELECT * FROM sys.dm_db_objects_disabled_on_version_change;  
GO  
```  
  
```  
class  class_desc        major_id    minor_id    dependency                       
------ ----------------- ----------- ----------- ----------   
1      OBJECT_OR_COLUMN  181575685   NULL        geometry                        
7      INDEX             37575172    1           geometry                        
7      INDEX             2121058592  1           geometry                        
1      OBJECT_OR_COLUMN  101575400   NULL        geometry     
```  
  
## <a name="remarks"></a>Notes  
  
### <a name="how-to-update-impacted-objects"></a>Procédure : mettre à jour les objets affectés  
 Les étapes ordonnées suivantes décrivent l'action corrective à entreprendre après la mise à niveau Service Release de juin.  
  
|JSON|Objet affecté|Action corrective|  
|-----------|---------------------|-----------------------|  
|1|**Index**|Reconstruisez tout index identifié par **sys.dm_db_objects_impacted_on_version_change** par exemple :  `ALTER INDEX ALL ON <table> REBUILD`<br />ou Gestionnaire de configuration<br />`ALTER TABLE <table> REBUILD`|  
|2|**Objet**|Toutes les contraintes identifiées par **sys.dm_db_objects_impacted_on_version_change** doivent être revalidées après que les données de géométrie et géographie dans la table sous-jacente sont recalculées. Pour les contraintes, revalidez l'aide de ALTER TABLE. <br />Exemple : <br />`ALTER TABLE <tab> WITH CHECK CHECK CONSTRAINT <constraint name>`<br />ou Gestionnaire de configuration<br />`ALTER TABLE <tab> WITH CHECK CONSTRAINT ALL`|  
  
  
