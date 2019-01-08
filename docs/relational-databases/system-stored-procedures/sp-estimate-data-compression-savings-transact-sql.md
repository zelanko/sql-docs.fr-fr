---
title: sp_estimate_data_compression_savings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_estimate_data_compression_savings_TSQL
- sp_estimate_data_compression_savings
dev_langs:
- TSQL
helpviewer_keywords:
- compression [SQL Server], estimating
- sp_estimate_data_compression_savings
ms.assetid: 6f6c7150-e788-45e0-9d08-d6c2f4a33729
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab1ed7614ff315986f38d497f00687784785790b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53213689"
---
# <a name="spestimatedatacompressionsavings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la taille actuelle de l'objet demandé et estime la taille de l'objet pour l'état de compression demandé. La compression peut être évaluée pour des tables entières ou des parties de tables. Cela inclut les segments de mémoire, les index ordonnés en clusters, index non cluster, index columnstore, indexées consulte, table et les partitions d’index. Les objets peuvent être compressées à l’aide de la compression d’archive ligne, page, columnstore ou columnstore. Si la table, l'index ou la partition sont déjà compressés, vous pouvez utiliser cette procédure pour estimer la taille de la table, de l'index ou de la partition s'ils sont décompressés.  
  
> [!NOTE]
>  La compression et **sp_estimate_data_compression_savings** ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Pour estimer la taille de l'objet s'il devait utiliser le paramètre de compression demandé, cette procédure stockée échantillonne l'objet source et charge ces données dans une table et un index équivalents, créés dans tempdb. La table ou l'index créés dans tempdb sont ensuite compressés au paramètre demandé et les gains de compression estimés sont calculés.  
  
 Pour modifier l’état de compression d’une table, l’index ou partition, utilisez le [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) ou [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) instructions. Pour obtenir des informations générales sur la compression, consultez [la Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
> [!NOTE]  
>  Si les données existantes sont fragmentées, vous pouvez être en mesure de réduire leur taille sans utiliser la compression en reconstruisant l'index. Pour les index, le facteur de remplissage sera appliqué pendant une reconstruction d'index. Cela pourrait augmenter la taille de l'index.  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_estimate_data_compression_savings   
     [ @schema_name = ] 'schema_name'    
   , [ @object_name = ] 'object_name'   
   , [@index_id = ] index_id   
   , [@partition_number = ] partition_number   
   , [@data_compression = ] 'data_compression'   
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @schema_name=] '*schema_name*'  
 Nom du schéma de base de données qui contient la table ou la vue indexée. *schema_name* est **sysname**. Si *schema_name* est NULL, le schéma par défaut de l’utilisateur actuel est utilisé.  
  
 [ @object_name=] '*object_name*'  
 Nom du schéma de la table ou de la vue indexée sur laquelle se trouve l'index. *object_name* est de type **sysname**.  
  
 [ @index_id=] '*index_id*'  
 Identificateur de l’index. *index_id* est **int**, et peut prendre l’une des valeurs suivantes : le numéro d’ID d’un index, NULL ou 0 si *object_id* est un segment de mémoire. Pour retourner des informations sur tous les index d'une table de base ou d'une vue, spécifiez la valeur NULL. Si vous spécifiez la valeur NULL, vous devez également spécifier NULL pour *partition_number*.  
  
 [ @partition_number=] '*partition_number*'  
 Numéro de partition dans l'objet. *partition_number* est **int**, et peut prendre l’une des valeurs suivantes : le numéro de partition d’un index ou segment de mémoire, NULL ou 1 pour un segment de mémoire ou un index non partitionné.  
  
 Pour spécifier la partition, vous pouvez également spécifier le [$partition](../../t-sql/functions/partition-transact-sql.md) (fonction). Pour retourner des informations pour toutes les partitions de l'objet propriétaire, spécifiez NULL.  
  
 [ @data_compression=] '*data_compression*'  
 Type de compression à évaluer. *DATA_COMPRESSION* peut prendre l’une des valeurs suivantes : NONE, ROW, PAGE, COLUMNSTORE ou COLUMNSTORE_ARCHIVE.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Le jeu de résultats suivant est retourné pour fournir la taille actuelle et estimée de la table, de l'index ou de la partition.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|Nom de la table ou de la vue indexée.|  
|schema_name|**sysname**|Schéma de la table ou de la vue indexée.|  
|index_id|**Int**|ID d'index d'un index :<br /><br /> 0 = Segment de mémoire<br /><br /> 1 = index cluster<br /><br /> > 1 = Index non cluster|  
|partition_number|**Int**|Numéro de partition. Retourne 1 pour une table ou un index non partitionnés.|  
|size_with_current_compression_setting (Ko)|**bigint**|Taille de la table, de l'index ou de la partition demandés tels qu'ils existent actuellement.|  
|size_with_requested_compression_setting (Ko)|**bigint**|Taille estimée de la table, de l'index ou de la partition qui utilise le paramètre de compression demandé et, le cas échéant, le facteur de remplissage existant, en supposant qu'il n'y a pas de fragmentation.|  
|sample_size_with_current_compression_setting (Ko)|**bigint**|Taille de l'exemple avec le paramètre de compression actuel. Cela inclut toute fragmentation éventuelle.|  
|sample_size_with_requested_compression_setting (Ko)|**bigint**|Taille de l'échantillon créé à l'aide du paramètre de compression demandé et, le cas échéant, du facteur de remplissage existant, sans fragmentation.|  
  
## <a name="remarks"></a>Notes  
 Utilisez sp_estimate_data_compression_savings pour estimer les économies qui peuvent se produire lorsque vous activez une table ou une partition pour la ligne, page, columnstore ou la compression d’archivage columnstore. Par exemple, si la taille moyenne de la ligne peut être réduite de 40 %, vous pouvez réduire la taille de l'objet de 40 %. Vous n'économiserez peut-être pas d'espace car cela dépend du facteur de remplissage et de la taille de la ligne. Par exemple, si vous disposez d'une ligne d'une longueur de 8 000 octets et que vous réduisez sa taille de 40 %, vous ne pouvez toujours pas intégrer plus d'une ligne dans une page de données. Vous ne bénéficiez d'aucun gain.  
  
 Si les résultats de l'exécution de sp_estimate_data_compression_savings indiquent que la taille de la table augmentera, cela signifie que de nombreuses lignes de la table utilisent quasiment la précision complète des types de données, et l'ajout de la faible surcharge requise pour le format compressé dépasse les gains dérivés de la compression. Dans ce cas très peu fréquent, n'activez pas la compression.  
  
 Si une table est activée pour la compression, utilisez sp_estimate_data_compression_savings pour estimer la taille moyenne de la ligne si la table est décompressée.  
  
 Un verrou (IS) est acquis sur la table pendant cette opération. Si un verrou (IS) ne peut pas être obtenu, la procédure sera bloquée. La table est analysée sous le niveau d'isolement de lecture validée.  
  
 Si le paramètre de compression demandé est identique au paramètre de compression actuel, la procédure stockée retournera la taille estimée sans fragmentation de données et en utilisant le facteur de remplissage existant.  
  
 Si l'ID d'index ou de partition n'existe pas, aucun résultat n'est retourné.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation SELECT sur la table.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Avant SQL Server 2019, cette procédure n’a pas été appliqué aux index columnstore et par conséquent n’a pas accepté les paramètres de compression de données COLUMNSTORE et COLUMNSTORE_ARCHIVE.  À compter de SQL Server 2019, index columnstore peuvent servir à la fois en tant qu’objet source pour l’estimation et un type de compression demandé.

## <a name="considerations-for-columnstore-indexes"></a>Considérations pour les index Columnstore
 En commençant par SQL Server 2019, sp_estimate_compression_savings prend en charge l’estimation de columnstore et compression d’archive de columnstore. Contrairement à la compression de page et de ligne, application de la compression de columnstore pour un objet requiert la création d’un nouvel index columnstore. Pour cette raison, lorsque vous utilisez les options de COLUMNSTORE et COLUMNSTORE_ARCHIVE de cette procédure, le type de l’objet de source fourni à la procédure détermine le type d’index columnstore utilisée pour l’évaluation de la taille compressée. Le tableau suivant illustre la référence d’objets utilisés pour estimer les économies de compression pour chaque objet de source de type quand le @data_compression paramètre est défini sur COLUMNSTORE ou COLUMNSTORE_ARCHIVE.

 |Objet source|Objet de référence|
 |-----------------|---------------|
 |Segment de mémoire (heap)|Index columnstore cluster|
 |Index cluster|Index columnstore cluster|
 |Index non cluster|Index columnstore non cluster (notamment les colonnes clés et colonnes incluses de l’index non cluster fourni, ainsi que la colonne de partition de la table, le cas échéant)|
 |Index columnstore non cluster|Index columnstore non cluster (y compris les mêmes colonnes que l’index fourni columnstore non cluster)|
 |Index columnstore cluster|Index columnstore cluster|

> [!NOTE]  
> Lors de l’estimation de la compression de columnstore d’un objet de source de rowstore (index cluster, index non cluster ou segment de mémoire), s’il existe des colonnes dans l’objet source qui ont un type de données qui n’est pas pris en charge dans un index columnstore, sp_estimate_compression_ économies échoue avec une erreur.

 De même, lorsque le @data_compression paramètre est défini sur NONE, ROW ou PAGE et l’objet source est un index columnstore, le tableau suivant présente les objets de référence utilisés.

 |Objet source|Objet de référence|
 |-----------------|---------------|
 |Index columnstore cluster|Segment de mémoire (heap)|
 |Index columnstore non cluster|Index non cluster (y compris les colonnes contenues dans l’index columnstore non cluster en tant que colonnes clés et la colonne de partition de la table, le cas échéant, en tant que colonne incluse)|

> [!NOTE]  
> Lors de l’estimation de la compression de rowstore (NONE, ligne ou PAGE) à partir d’un objet de source de columnstore, n’oubliez pas que l’index de la source ne contienne pas plus de 32 colonnes car c’est la limite prise en charge dans un index (non cluster) de rowstore.
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous estime la taille de la table `Production.WorkOrderRouting` si elle est compressée à l'aide de la compression `ROW`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimate_data_compression_savings 'Production', 'WorkOrderRouting', NULL, NULL, 'ROW' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Implémentation de la compression Unicode](../../relational-databases/data-compression/unicode-compression-implementation.md)  
  
  
