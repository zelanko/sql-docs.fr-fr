---
title: sp_addarticle (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addarticle
- sp_addarticle_TSQL
helpviewer_keywords:
- sp_addarticle
ms.assetid: 0483a157-e403-4fdb-b943-23c1b487bef0
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6f24f7ca51f4836c8b1e446283eabb858eb8d387
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493891"
---
# <a name="spaddarticle-transact-sql"></a>sp_addarticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un article et l'ajoute à une publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addarticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
    [ , [ @source_table = ] 'source_table' ]  
    [ , [ @destination_table = ] 'destination_table' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @type = ] 'type' ]   
    [ , [ @filter = ] 'filter' ]   
    [ , [ @sync_object= ] 'sync_object' ]   
        [ , [ @ins_cmd = ] 'ins_cmd' ]   
    [ , [ @del_cmd = ] 'del_cmd' ]   
        [ , [ @upd_cmd = ] 'upd_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @filter_clause = ] 'filter_clause' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @status = ] status ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @sync_object_owner = ] 'sync_object_owner' ]   
    [ , [ @filter_owner = ] 'filter_owner' ]   
    [ , [ @source_object = ] 'source_object' ]   
    [ , [ @artid = ] article_ID  OUTPUT ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @use_default_datatypes = ] use_default_datatypes  
    [ , [ @identityrangemanagementoption = ] identityrangemanagementoption ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @fire_triggers_on_snapshot = ] 'fire_triggers_on_snapshot' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication contenant l’article. Le nom doit être unique dans la base de données. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'` Est le nom de l’article. Le nom doit être unique dans la publication. *article* est **sysname**, sans valeur par défaut.  
  
`[ @source_table = ] 'source_table'` Ce paramètre est déconseillé ; Utilisez *source_object* à la place.  
  
 *Ce paramètre n’est pas pris en charge pour les serveurs de publication Oracle.*  
  
`[ @destination_table = ] 'destination_table'` Est le nom de la table de destination (abonnement), s’il diffère *source_table*ou la procédure stockée. *destination_table* est **sysname**, avec NULL comme valeur par défaut, ce qui signifie que *source_table* est égal à *destination_table **.*  
  
`[ @vertical_partition = ] 'vertical_partition'` Active et désactive le filtrage de colonne sur un article de table. *partition_verticale* est **nchar(5)**, avec FALSE comme valeur par défaut.  
  
 **false** indique l’absence de filtrage vertical et publie toutes les colonnes.  
  
 **true** efface toutes les colonnes à l’exception de la clé primaire déclarée, sans valeur par défaut des colonnes de type nullable et les colonnes de clé uniques. Les colonnes sont ajoutées à l’aide de [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md).  
  
`[ @type = ] 'type'` Est le type d’article. *type* est **sysname**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**schéma d’agrégation uniquement**|Fonction d'agrégation avec schéma uniquement|  
|**schéma de Func uniquement**|Fonction avec schéma uniquement.|  
|**logbased de vue indexée**|Article de vue indexée reposant sur un journal. Non pris en charge pour les serveurs de publication Oracle. Pour ce type d'article, il n'est pas nécessaire de publier la table de base séparément.|  
|**la vue indexée logbased manualboth**|Article de vue indexée reposant sur un journal avec filtre manuel et vue manuelle. Cette option nécessite que vous spécifiez à la fois *sync_object* et *filtre* paramètres. Pour ce type d'article, il n'est pas nécessaire de publier la table de base séparément. Non pris en charge pour les serveurs de publication Oracle.|  
|**la vue indexée logbased manualfilter**|Article de vue indexée reposant sur un journal avec filtre manuel. Cette option nécessite que vous spécifiez à la fois *sync_object* et *filtre* paramètres. Pour ce type d'article, il n'est pas nécessaire de publier la table de base séparément. Non pris en charge pour les serveurs de publication Oracle.|  
|**la vue indexée logbased manualview**|Article de vue indexée reposant sur un journal avec vue manuelle. Cette option requiert que vous spécifiiez le *sync_object* paramètre. Pour ce type d'article, il n'est pas nécessaire de publier la table de base séparément. Non pris en charge pour les serveurs de publication Oracle.|  
|**schéma de vue indexée uniquement**|Vue indexée avec schéma uniquement. Pour ce type d'article, la table de base doit également être publiée.|  
|**logbased** (valeur par défaut)|Article basé sur le journal.|  
|**logbased manualboth**|Article reposant sur un journal, avec filtre manuel et vue manuelle. Cette option nécessite que vous spécifiez à la fois *sync_object* et *filtre* paramètres. Non pris en charge pour les serveurs de publication Oracle.|  
|**logbased manualfilter**|Article reposant sur un journal, avec filtre manuel. Cette option nécessite que vous spécifiez à la fois *sync_object* et *filtre* paramètres. Non pris en charge pour les serveurs de publication Oracle.|  
|**logbased manualview**|Article reposant sur un journal, avec vue manuelle. Cette option requiert que vous spécifiiez le *sync_object* paramètre. Non pris en charge pour les serveurs de publication Oracle.|  
|**proc exec**|Réplique l'exécution de la procédure stockée pour tous les abonnés de l'article. Non pris en charge pour les serveurs de publication Oracle. Nous vous recommandons d’utiliser l’option **serializable proc exec** au lieu de **proc exec**. Pour plus d’informations, consultez la section « Types de stockées procédure Articles d’exécution » dans [Publishing Stored Procedure Execution dans la réplication transactionnelle](../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md). Non disponible lorsque la capture de données modifiées est activée.|  
|**proc schéma uniquement**|Procédure avec schéma uniquement. Non pris en charge pour les serveurs de publication Oracle.|  
|**serializable proc exec**|Réplique l'exécution de la procédure stockée uniquement si l'exécution se fait dans le contexte d'une transaction compatible avec la mise en série. Non pris en charge pour les serveurs de publication Oracle.<br /><br /> La procédure doit également être exécutée dans une transaction explicite pour l’exécution de la procédure de réplication.|  
|**afficher le schéma uniquement**|Vue avec schéma uniquement. Non pris en charge pour les serveurs de publication Oracle. Lorsque vous utilisez cette option, vous devez aussi publier la table de base.|  
  
`[ @filter = ] 'filter'` La procédure stockée (créée avec FOR REPLICATION) permet de filtrer la table horizontalement. *filtre* est **nvarchar (386)**, avec NULL comme valeur par défaut. [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) et [sp_articlefilter](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) doit être exécutée manuellement pour créer la vue et la procédure stockée de filtre. Si la valeur par défaut n'est pas NULL, la procédure de filtre n'est pas créée (cela suppose que la procédure stockée est créée manuellement).  
  
`[ @sync_object = ] 'sync_object'` Est le nom de la table ou la vue utilisée pour produire le fichier de données utilisé pour représenter la capture instantanée de cet article. *sync_object* est **nvarchar (386)**, avec NULL comme valeur par défaut. Si NULL, [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) est appelée pour créer automatiquement la vue utilisée pour générer le fichier de sortie. Cela se produit après l’ajout de toutes les colonnes avec [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Si la valeur par défaut n'est pas NULL, aucune vue n'est créée (cela suppose que la vue est créée manuellement).  
  
`[ @ins_cmd = ] 'ins_cmd'` Est le type de commande de réplication utilisé pour répliquer des insertions pour cet article. *ins_cmd* est **nvarchar (255)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**NONE**|Aucune action n'est effectuée.|  
|**CALL sp_MSins_**<br /> **_table_**  (default)<br /><br /> -ou-<br /><br /> **APPEL custom_stored_procedure_name**|Appelle l'exécution d'une procédure stockée sur l'Abonné. Pour utiliser cette méthode de réplication, utilisez *schema_option* pour spécifier la création automatique de la procédure stockée, ou créer la procédure stockée spécifiée dans la base de données de destination de chaque abonné de l’article. *custom_stored_procedure* est le nom d’une procédure stockée créée par l’utilisateur. <strong>sp_Msins_*table*</strong>  contient le nom de la table de destination à la place de la *_table* dans le cadre du paramètre. Lorsque *destination_owner* est spécifié, il est ajouté devant le nom de table de destination. Par exemple, pour le **ProductCategory** table détenue par le **Production** schéma sur l’abonné, le paramètre serait `CALL sp_MSins_ProductionProductCategory`. Pour un article dans une topologie de réplication d’égal à égal, *_table* est ajouté avec une valeur GUID. Spécification *custom_stored_procedure* n’est pas pris en charge pour la mise à jour des abonnés.|  
|**SQL** ou NULL|Réplique une instruction INSERT. Des valeurs sont fournies pour l'instruction INSERT pour l'ensemble des colonnes publiées dans l'article. La commande suivante est répliquée lors des insertions :<br /><br /> `INSERT INTO <table name> VALUES (c1value, c2value, c3value, ..., cnvalue)`|  
  
 Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
`[ @del_cmd = ] 'del_cmd'` Est le type de commande de réplication utilisé pour répliquer des suppressions pour cet article. *del_cmd* est **nvarchar (255)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**NONE**|Aucune action n'est effectuée.|  
|**CALLsp_MSdel_**<br /> **_table_**  (default)<br /><br /> -ou-<br /><br /> **APPEL custom_stored_procedure_name**|Appelle l'exécution d'une procédure stockée sur l'Abonné. Pour utiliser cette méthode de réplication, utilisez *schema_option* pour spécifier la création automatique de la procédure stockée, ou créer la procédure stockée spécifiée dans la base de données de destination de chaque abonné de l’article. *custom_stored_procedure* est le nom d’une procédure stockée créée par l’utilisateur. <strong>sp_Msdel_*table*</strong>  contient le nom de la table de destination à la place de la *_table* dans le cadre du paramètre. Lorsque *destination_owner* est spécifié, il est ajouté devant le nom de table de destination. Par exemple, pour le **ProductCategory** table détenue par le **Production** schéma sur l’abonné, le paramètre serait `CALL sp_MSdel_ProductionProductCategory`. Pour un article dans une topologie de réplication d’égal à égal, *_table* est ajouté avec une valeur GUID. Spécification *custom_stored_procedure* n’est pas pris en charge pour la mise à jour des abonnés.|  
|**XCALL sp_MSdel_**<br /> **_table_**<br /><br /> -ou-<br /><br /> **XCALL custom_stored_procedure_name**|Appelle une procédure stockée utilisant des paramètres de type XCALL. Pour utiliser cette méthode de réplication, utilisez *schema_option* pour spécifier la création automatique de la procédure stockée, ou créer la procédure stockée spécifiée dans la base de données de destination de chaque abonné de l’article. La spécification d'une procédure stockée créée par l'utilisateur n'est pas autorisée pour mettre à jour les Abonnés.|  
|**SQL** ou NULL|Réplique une instruction DELETE. Toutes les valeurs de colonnes clés primaire sont fournies pour l'instruction DELETE. La commande suivante est répliquée lors des suppressions :<br /><br /> `DELETE FROM <table name> WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
 Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
`[ @upd_cmd = ] 'upd_cmd'` Est le type de commande de réplication utilisé lors de la réplication des mises à jour pour cet article. *upd_cmd* est **nvarchar (255)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**NONE**|Aucune action n'est effectuée.|  
|**CALL sp_MSupd_**<br /> **_table_**<br /><br /> -ou-<br /><br /> **APPEL custom_stored_procedure_name**|Appelle l'exécution d'une procédure stockée sur l'Abonné. Pour utiliser cette méthode de réplication, utilisez *schema_option* pour spécifier la création automatique de la procédure stockée, ou créer la procédure stockée spécifiée dans la base de données de destination de chaque abonné de l’article.|  
|**MCALL sp_MSupd_**<br /> **_table_**<br /><br /> -ou-<br /><br /> **MCALL custom_stored_procedure_name**|Appelle une procédure stockée utilisant des paramètres de type MCALL. Pour utiliser cette méthode de réplication, utilisez *schema_option* pour spécifier la création automatique de la procédure stockée, ou créer la procédure stockée spécifiée dans la base de données de destination de chaque abonné de l’article. *custom_stored_procedure* est le nom d’une procédure stockée créée par l’utilisateur. <strong>sp_Msupd_*table*</strong>  contient le nom de la table de destination à la place de la *_table* dans le cadre du paramètre. Lorsque *destination_owner* est spécifié, il est ajouté devant le nom de table de destination. Par exemple, pour le **ProductCategory** table détenue par le **Production** schéma sur l’abonné, le paramètre serait `MCALL sp_MSupd_ProductionProductCategory`. Pour un article dans une topologie de réplication d’égal à égal, *_table* est ajouté avec une valeur GUID. La spécification d'une procédure stockée créée par l'utilisateur n'est pas autorisée pour mettre à jour les Abonnés.|  
|**SCALL sp_MSupd_**<br /> **_table_**  (default)<br /><br /> -ou-<br /><br /> **SCALL custom_stored_procedure_name**|Appelle une procédure stockée utilisant des paramètres de type SCALL. Pour utiliser cette méthode de réplication, utilisez *schema_option* pour spécifier la création automatique de la procédure stockée, ou créer la procédure stockée spécifiée dans la base de données de destination de chaque abonné de l’article. *custom_stored_procedure* est le nom d’une procédure stockée créée par l’utilisateur. <strong>sp_Msupd_*table*</strong>  contient le nom de la table de destination à la place de la *_table* dans le cadre du paramètre. Lorsque *destination_owner* est spécifié, il est ajouté devant le nom de table de destination. Par exemple, pour le **ProductCategory** table détenue par le **Production** schéma sur l’abonné, le paramètre serait `SCALL sp_MSupd_ProductionProductCategory`. Pour un article dans une topologie de réplication d’égal à égal, *_table* est ajouté avec une valeur GUID. La spécification d'une procédure stockée créée par l'utilisateur n'est pas autorisée pour mettre à jour les Abonnés.|  
|**XCALL sp_MSupd_**<br /> **_table_**<br /><br /> -ou-<br /><br /> **XCALL custom_stored_procedure_name**|Appelle une procédure stockée utilisant des paramètres de type XCALL. Pour utiliser cette méthode de réplication, utilisez *schema_option* pour spécifier la création automatique de la procédure stockée, ou créer la procédure stockée spécifiée dans la base de données de destination de chaque abonné de l’article. La spécification d'une procédure stockée créée par l'utilisateur n'est pas autorisée pour mettre à jour les Abonnés.|  
|**SQL** ou NULL|Réplique une instruction UPDATE. L'instruction UPDATE est fournie pour toutes les valeurs des colonnes et toutes les valeurs de colonne clé primaire. La commande ci-dessous est répliquée lors des mises à jour :<br /><br /> `UPDATE <table name> SET c1 = c1value, SET c2 = c2value, SET cn = cnvalue WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
> [!NOTE]  
>  Les syntaxes CALL, MCALL, SCALL et XCALL déterminent la quantité de données diffusée à l'abonné. La syntaxe CALL transmet toutes les valeurs de toutes les colonnes insérées et supprimées. La syntaxe SCALL transmet uniquement les valeurs des colonnes affectées. La syntaxe XCALL transmet les valeurs de toutes les colonnes, modifiées ou non, y compris leurs valeurs précédentes. Pour plus d’informations, consultez [Spécifier le mode de propagation des modifications des articles transactionnels](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
`[ @creation_script = ] 'creation_script'` Est le chemin d’accès et le nom d’un script de schéma d’article facultatif utilisé pour créer l’article dans la base de données d’abonnement. *creation_script* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
`[ @description = ] 'description'` Est une entrée descriptive de l’article. *Description* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
`[ @pre_creation_cmd = ] 'pre_creation_cmd'` Spécifie que le système doit faire s’il détecte un objet existant du même nom sur l’abonné lors de l’application de la capture instantanée de cet article. *pre_creation_cmd* est **nvarchar (10)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**None**|N'utilise pas de commande.|  
|**delete**|Supprime les données de la table de destination avant d'appliquer l'instantané. Lorsque l'article est filtré horizontalement, seules les données qui se trouvent dans les colonnes spécifiées par la clause filter sont supprimées. Non pris en charge pour les serveurs de publication Oracle lorsqu'un filtre horizontal est défini.|  
|**DROP** (valeur par défaut)|Supprime la table de destination.|  
|**truncate**|Tronque la table de destination. N'est pas valide pour les abonnés ODBC ou OLE DB.|  
  
`[ @filter_clause = ] 'filter_clause'` Est une restriction clause (WHERE) qui définit un filtre horizontal. Lorsque vous entrez la clause de restriction, omettez le mot clé où. *filter_clause* est **ntext**, avec NULL comme valeur par défaut. Pour plus d’informations, consultez [Filtrer des données publiées](../../relational-databases/replication/publish/filter-published-data.md).  
  
`[ @schema_option = ] schema_option` Est un masque de bits de l’option de génération de schéma pour l’article donné. *schema_option* est **Binary (8)** et peut être le [| (OR au niveau du bit) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) produit d’une ou plusieurs des valeurs suivantes :  
  
> [!NOTE]  
>  Si la valeur est NULL, le système génère automatiquement une option de schéma valide pour l'article en fonction des autres propriétés de l'article. Le **par défaut des Options de schéma** table donné la section Notes montre la valeur qui sera choisie en fonction de la combinaison de type d’article et le type de réplication.  
  
|Value|Description|  
|-----------|-----------------|  
|**0x00**|Désactive la génération de scripts par l’Agent d’instantané et utilise *creation_script*.|  
|**0x01**|Génère le script de création d'objet (CREATE TABLE, CREATE PROCEDURE, etc.). Cette valeur est la valeur par défaut pour les articles de procédure stockée.|  
|**0x02**|Génère les procédures stockées qui propagent les modifications pour l'article, si elles sont définies.|  
|**0x04**|Les colonnes d'identité font l'objet d'un script utilisant la propriété IDENTITY.|  
|**0x08**|Répliquer **timestamp** colonnes. Si ce n’est pas définie, **timestamp** les colonnes sont répliquées en tant que **binaire**.|  
|**0x10**|Génère un index cluster correspondant. Même si cette option n'est pas activée, les index relatifs aux clés primaires et aux contraintes uniques sont générés s'ils sont déjà définis sur une table publiée.|  
|**0x20**|Convertit les types de données définis par l'utilisateur (UDT) en types de données de base auprès de l'Abonné. Vous ne pouvez pas utiliser cette option lorsqu'il existe une contrainte CHECK ou DEFAULT sur une colonne de type défini par l'utilisateur (UDT), si une colonne UDT fait partie de la clé primaire, ou si une colonne calculée désigne une colonne UDT. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**0x40**|Génère les index non-cluster correspondants. Même si cette option n'est pas activée, les index relatifs aux clés primaires et aux contraintes uniques sont générés s'ils sont déjà définis sur une table publiée.|  
|**0x80**|Réplique les contraintes de clé primaire. Tous les index relatifs à la contrainte sont également répliqués, même si options **0 x 10** et **0 x 40** ne sont pas activés.|  
|**0x100**|Réplique les déclencheurs utilisateur, si ceux-ci sont définis, sur un article de table. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**0x200**|Réplique les contraintes de clés étrangères. Si la table référencée ne fait pas partie d'une publication, aucune contrainte de clé étrangère appliquée à une table publiée n'est répliquée. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**0x400**|Réplique les contraintes de vérification. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**0x800**|Réplique les valeurs par défaut. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**0x1000**|Réplique le classement au niveau des colonnes.<br /><br /> **Remarque :** Cette option doit être définie pour les serveurs de publication Oracle afin d'activer les comparaisons qui respectent la casse.|  
|**0x2000**|Réplique les propriétés étendues associées à l'objet source de l'article publié. *Non pris en charge pour les serveurs de publication Oracle*.|  
|**0x4000**|Réplique les contraintes UNIQUE. Tous les index relatifs à la contrainte sont également répliqués, même si options **0 x 10** et **0 x 40** ne sont pas activés.|  
|**0x8000**|Cette option n'est pas valide pour les serveurs de publication [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000**|Réplique les contraintes CHECK en tant que NOT FOR REPLICATION afin que les contraintes ne soient pas appliquées durant la synchronisation.|  
|**0x20000**|Réplique les contraintes FOREIGN KEY en tant que NOT FOR REPLICATION afin que les contraintes ne soient pas appliquées durant la synchronisation.|  
|**0x40000**|Réplique les groupes de fichiers associés à une table ou un index partitionné.|  
|**0x80000**|Réplique le schéma de partition d'une table partitionnée.|  
|**0x100000**|Réplique le schéma de partition d'un index partitionné.|  
|**0x200000**|Réplique les statistiques d'une table.|  
|**0x400000**|Liaisons par défaut|  
|**0x800000**|Liaisons de règle|  
|**0x1000000**|Index de recherche en texte intégral|  
|**0x2000000**|Collections de schéma XML liées aux **xml** colonnes ne sont pas répliquées.|  
|**0x4000000**|Réplique les index sur **xml** colonnes.|  
|**0x8000000**|Crée tout schéma non encore présent chez l'abonné.|  
|**0x10000000**|Convertit **xml** colonnes à **ntext** sur l’abonné.|  
|**0x20000000**|Types de données de l’objet convertit volumineux (**nvarchar (max)**, **varchar (max)**, et **varbinary (max)**) introduite dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] aux types de données qui sont prises en charge sur [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|Réplique les autorisations.|  
|**0x80000000**|Tente de supprimer les dépendances envers tous les objets qui ne font pas partie de la publication.|  
|**0x100000000**|Utilisez cette option pour répliquer l’attribut FILESTREAM s’il est spécifié sur **varbinary (max)** colonnes. Ne spécifiez pas cette option si vous répliquez des tables sur des Abonnés [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. La réplication de tables qui possèdent des colonnes FILESTREAM sur [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] abonnés n'est pas pris en charge, quelle que soit la façon dont cette option de schéma est définie.<br /><br /> Consultez l’option connexe **0 x 800000000**.|  
|**0x200000000**|Convertit les types de données de date et heure (**date**, **temps**, **datetimeoffset**, et **datetime2**) introduite dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] aux données les types qui sont pris en charge sur les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**0x400000000**|Réplique l'option de compression pour les données et les index. Pour plus d’informations, consultez [Compression de données](../../relational-databases/data-compression/data-compression.md).|  
|**0x800000000**|Définissez cette option pour stocker les données FILESTREAM dans leur propre groupe de fichiers sur l'Abonné. Si cette option n'est pas définie, les données FILESTREAM sont stockées dans le groupe de fichiers par défaut. La réplication ne crée pas de groupes de fichiers ; par conséquent, si vous définissez cette option, vous devez créer le groupe de fichiers avant d'appliquer l'instantané à l'Abonné. Pour plus d’informations sur la création d’objets avant d’appliquer l’instantané, consultez [exécuter des Scripts avant et après l’instantané est appliqué](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).<br /><br /> Consultez l’option connexe **0 x 100000000**.|  
|**0x1000000000**|Convertit les types common language runtime (CLR) défini par l’utilisateur (UDT) supérieurs à 8 000 octets pour **varbinary (max)** afin que les colonnes de type UDT puissent être répliquées sur les abonnés qui sont en cours d’exécution [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x2000000000**|Convertit le **hierarchyid** type de données à **varbinary (max)** afin que les colonnes de type **hierarchyid** peuvent être répliquées sur les abonnés qui sont en cours d’exécution [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour plus d’informations sur l’utilisation **hierarchyid** colonnes dans les tables répliquées, consultez [hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
|**0x4000000000**|Réplique tous les index filtrés sur la table. Pour plus d’informations sur les index filtrés, consultez [créer des index filtrés](../../relational-databases/indexes/create-filtered-indexes.md).|  
|**0x8000000000**|Convertit le **geography** et **geometry** types de données **varbinary (max)** afin que les colonnes de ces types peuvent être répliquées sur les abonnés qui sont en cours d’exécution [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|Réplique les index sur des colonnes de type **geography** et **geometry**.|  
|**0x20000000000**|Réplique l'attribut SPARSE pour les colonnes. Pour plus d’informations sur cet attribut, consultez [utiliser des colonnes éparses](../../relational-databases/tables/use-sparse-columns.md).|  
|**0x40000000000**|Activer la génération de scripts par l’agent d’instantané pour créer la table optimisée en mémoire sur l’abonné.|  
|**0x80000000000**|Convertit un index cluster en index non cluster pour les articles optimisés en mémoire.|  
|**0x400000000000**|Réplique tous les index columnstore non cluster sur l’ou les tables|  
|**0x800000000000**|Réplique tous flitered les index columnstore non cluster sur l’ou les tables.|  
|NULL|La réplication définit automatiquement *schema_option* à une valeur par défaut, dont la valeur dépend d’autres propriétés de l’article. Le tableau « Options de schéma par défaut » de la section Notes montre les options de schéma par défaut en fonction du type d'article et du type de réplication.<br /><br /> La valeur par défaut pour les non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publications est **0x050D3**.|  
  
 Pas tous *schema_option* valeurs sont valides pour chaque type de réplication et le type d’article. Le **les Options de schéma valides** table dans la section Notes montre les options de schéma valides qui peuvent être sélectionnées en fonction de la combinaison de type d’article et le type de réplication.  
  
`[ @destination_owner = ] 'destination_owner'` Est le nom du propriétaire de l’objet de destination. *destination_owner* est **sysname**, avec NULL comme valeur par défaut. Lorsque *destination_owner* n’est pas spécifié, le propriétaire est spécifié automatiquement selon les règles suivantes :  
  
|Condition|Propriétaire de l'objet de destination|  
|---------------|------------------------------|  
|La publication utilise la copie en bloc en mode natif pour générer l'instantané initial, qui prend uniquement en charge des Abonnés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Par défaut la valeur de *lui*.|  
|Publié à partir d'un serveur de publication non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Devient par défaut propriétaire de la base de données de destination.|  
|La publication utilise la copie en bloc en mode caractère pour générer l'instantané initial, qui prend en charge des Abonnés non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Non assigné.|  
  
 Pour prendre en charge non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés, *destination_owner* doit être NULL.  
  
`[ @status = ] status` Spécifie si l’article est actives et des options supplémentaires pour propager les modifications. *état* est **tinyint**et peut être le [| (OR au niveau du bit) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) produit d’une ou plusieurs des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Article actif|  
|**8**|Inclut le nom de colonne dans les instructions INSERT.|  
|**16** (valeur par défaut)|Utilise des instructions paramétrables.|  
|**24**|Inclut le nom de colonne dans les instructions INSERT et utilise des instructions paramétrables.|  
|**64**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 Par exemple, un article actif utilisant des instructions paramétrables posséderait la valeur 17 dans cette colonne. La valeur **0** signifie que l’article est inactif et qu’aucune propriété supplémentaire est définie.  
  
`[ @source_owner = ] 'source_owner'` Est le propriétaire de l’objet source. *lui* est **sysname**, avec NULL comme valeur par défaut. *lui* doit être spécifié pour les serveurs de publication Oracle.  
  
`[ @sync_object_owner = ] 'sync_object_owner'` Est le propriétaire de la vue qui définit l’article publié. *lui* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @filter_owner = ] 'filter_owner'` Est le propriétaire du filtre. *lui* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @source_object = ] 'source_object'` Est l’objet de base de données à publier. *source_object* est **sysname**, avec NULL comme valeur par défaut. Si *source_table* est NULL, *source_object* ne peut pas être NULL. *source_object* doit être utilisé au lieu de *source_table*. Pour plus d’informations sur les types d’objets qui peuvent être publiés à l’aide de la réplication d’instantané ou transactionnelle, consultez [publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
`[ @artid = ] _article_ID_ OUTPUT` Est l’ID de l’article du nouvel article. *article_id* est **int** avec la valeur par défaut est NULL et il est un paramètre de sortie.  
  
`[ @auto_identity_range = ] 'auto_identity_range'` Active et désactive la gestion sur une publication lors de la création de plages d’identité automatique. *auto_identity_range* est **nvarchar (5)**, et peut prendre l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**true**|Active la gestion automatique des plages d'identité|  
|**false**|Désactive la gestion automatique des plages d'identité|  
|NULL(Default)|Gestion de plages d’identité est définie par *identityrangemanagementoption*.|  
  
> [!NOTE]  
>  *auto_identity_range* a été déconseillée et est fourni pour la compatibilité descendante uniquement. Vous devez utiliser *identityrangemanagementoption* pour spécifier les options de gestion de plage identité. Pour plus d’informations, consultez [ Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @pub_identity_range = ] pub_identity_range` Contrôle la taille de plage sur le serveur de publication si l’article a *identityrangemanagementoption* définie sur **automatique** ou *auto_identity_range* la valeur **true** . *pub_identity_range* est **bigint**, avec NULL comme valeur par défaut. *Non pris en charge pour les serveurs de publication Oracle*.  
  
`[ @identity_range = ] identity_range` Contrôle la taille de plage sur l’abonné si l’article a *identityrangemanagementoption* définie sur **automatique** ou *auto_identity_range* la valeur **true** . *identity_range* est **bigint**, avec NULL comme valeur par défaut. Utilisé lorsque *auto_identity_range* a la valeur **true**. *Non pris en charge pour les serveurs de publication Oracle*.  
  
`[ @threshold = ] threshold` Est la valeur de pourcentage qui contrôle le moment où l’Agent de Distribution affecte une nouvelle plage d’identité. Lorsque le pourcentage de valeurs spécifié dans *seuil* est utilisé, l’Agent de Distribution crée une nouvelle plage d’identité. *seuil* est **bigint**, avec NULL comme valeur par défaut. Utilisé lorsque *identityrangemanagementoption* a la valeur **automatique** ou *auto_identity_range* a la valeur **true**. *Non pris en charge pour les serveurs de publication Oracle*.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Confirme que l’action entreprise par cette procédure stockée peut invalider un instantané existant. *àce_invalidate_snapshot* est un **bits**, avec 0 comme valeur par défaut.  
  
 **0** indique que l’ajout d’un article n’entraîne pas l’instantané n’est pas valide. Si la procédure stockée détecte que la modification requiert un nouvel instantané, un message d'erreur est généré et aucune modification n'est effectuée.  
  
 **1** Spécifie qu’Ajout d’un article peut-être invalider l’instantané n’est pas valide, et si des abonnements existent qui nécessiterait un nouvel instantané, donne l’autorisation de l’instantané existant soit marqué comme obsolète et un nouvel instantané doit être généré.  
  
`[ @use_default_datatypes = ] use_default_datatypes` Est si les mappages de type de données de colonne par défaut sont utilisées lors de la publication d’un article à partir d’un serveur de publication Oracle. *use_default_datatypes* est de type bit, avec 1 comme valeur par défaut.  
  
 **1** = la colonne d’article par défaut mappages sont utilisés. Les mappages de type de données par défaut peuvent être affichées en exécutant [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **0** = colonne d’article personnalisé les mappages sont définis, et par conséquent [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) n’est pas appelée par **sp_addarticle**.  
  
 Lorsque *use_default_datatypes* a la valeur **0**, vous devez exécuter [sp_changearticlecolumndatatype](../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md) une fois pour chaque mappage de colonne en cours de modification à partir de la valeur par défaut. Après ont défini tous les mappages de colonne personnalisée, vous devez exécuter [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md).  
  
> [!NOTE]  
>  Ce paramètre ne doit être utilisé que pour les serveurs de publication Oracle. Paramètre *use_default_datatypes* à **0** pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher génère une erreur.  
  
`[ @identityrangemanagementoption = ] identityrangemanagementoption` Spécifie les modalités de gestion de plage d’identité pour l’article. *identityrangemanagementoption* est **nvarchar (10)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**None**|La réplication n'explicite pas la gestion des plages d'identité. Cette option est recommandée uniquement pour la compatibilité ascendante avec des versions antérieures de SQL Server. Non autorisé pour la réplication d'homologue.|  
|**manual**|Marque la colonne d'identité en utilisant NOT FOR REPLICATION pour activer la gestion manuelle des plages d'identité.|  
|**auto**|Spécifie la gestion automatique des plages d'identité.|  
|NULL(Default)|Valeur par défaut est **aucun** lorsque la valeur de *auto_identity_range* n’est pas **true**. Valeur par défaut est **manuelle** dans une valeur par défaut de la topologie d’égal à égal (*auto_identity_range* est ignoré).|  
  
 Pour la compatibilité descendante, lorsque la valeur de *identityrangemanagementoption* est NULL, la valeur de *auto_identity_range* est activée. Toutefois, lorsque la valeur de *identityrangemanagementoption* n’est pas NULL, alors la valeur de *auto_identity_range* est ignoré.  
  
 Pour plus d’informations, consultez [ Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @publisher = ] 'publisher'` Spécifie un non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé lors de l’ajout d’un article à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
`[ @fire_triggers_on_snapshot = ] 'fire_triggers_on_snapshot'` Est si répliquées déclencheurs de l’utilisateur sont exécutés lorsque l’instantané initial est appliqué. *fire_triggers_on_snapshot* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **true** signifie que les déclencheurs utilisateur sur une table répliquée sont exécutés lorsque l’instantané est appliqué. Dans l’ordre des déclencheurs de réplication, la valeur de masque de bits de *schema_option* doit inclure la valeur **0 x 100**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addarticle** est utilisé dans la réplication d’instantané ou réplication transactionnelle.  
  
 Par défaut, la réplication ne publie aucune colonne dans la table source lorsque le type de données de colonne n'est pas pris en charge par la réplication. Si vous avez besoin publier une telle colonne, vous devez exécuter [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) pour ajouter la colonne.  
  
 Lors de l'ajout d'un article à une publication qui prend en charge la réplication transactionnelle d'homologue à homologue, les restrictions suivantes s'appliquent :  
  
-   Les instructions paramétrables doivent être spécifiées pour tous les articles logbased. Vous devez inclure **16** dans le *état* valeur.  
  
-   Le nom et le propriétaire de la table de destination doivent correspondre à la table source.  
  
-   Il est impossible de filtrer l'article horizontalement ou verticalement.  
  
-   La gestion automatique des plages d'identité n'est pas prise en charge. Vous devez spécifier une valeur manuelle pour *identityrangemanagementoption*.  
  
-   Si un **timestamp** colonne existe dans la table, vous devez inclure 0 x 08 dans *schema_option* pour répliquer la colonne en tant que **timestamp**.  
  
-   La valeur **SQL** ne peut pas être spécifié pour *ins_cmd*, *upd_cmd*, et *del_cmd*.  
  
 Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 Lorsque vous publiez des objets, leurs définitions sont copiées sur les abonnés. Si vous publiez un objet de base de données qui dépend d'un ou de plusieurs autres objets, vous devez publier tous les objets référencés. Par exemple, si vous publiez une vue qui dépend d'une table, vous devez publier la table également.  
  
 Si *partition_verticale* a la valeur **true**, **sp_addarticle** diffère la création de la vue jusqu'à [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) est appelée (après la dernière [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) est ajouté).  
  
 Si la publication autorise la mise à jour des abonnements et la table publiée n’a pas un **uniqueidentifier** colonne, **sp_addarticle** ajoute un **uniqueidentifier** colonne à la table automatiquement.  
  
 Lors de la réplication vers un abonné qui n’est pas une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (réplication hétérogène), uniquement [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions sont prises en charge pour **insérer**, **mise à jour**et **Supprimer** commandes.  
  
 Lorsque l'Agent de lecture du journal s'exécute, l'ajout d'un article à une publication d'égal à égal peut provoquer un interblocage entre l'Agent de lecture du journal et le processus qui ajoute l'article. Pour éviter ce problème, avant d'ajouter un article à une publication d'égal à égal, utilisez le moniteur de réplication afin d'arrêter l'Agent de lecture du journal sur le nœud où vous ajoutez l'article. Redémarrez l'Agent de lecture du journal après l'ajout de l'article.  
  
 Lors de la définition `@del_cmd = 'NONE'` ou `@ins_cmd = 'NONE'`, la propagation de **mettre à jour** commandes peuvent aussi être affectés en n’envoyant ne pas ces commandes lorsqu’une mise à jour associée se produit. (Une mise à jour associée est un type d'instruction UPDATE du serveur de publication qui réplique comme une paire de DELETE/INSERT sur l'abonné.)  
  
## <a name="default-schema-options"></a>Options de schéma par défaut  
 Ce tableau décrit la valeur par défaut définie par la réplication si *schema_options* n’est pas spécifié par l’utilisateur, où cette valeur varie selon le type de réplication (dans la partie supérieure) et le type d’article (dans la première colonne).  
  
|Type de l'article|Type de réplication||  
|------------------|----------------------|------|  
||Transactionnelle|Snapshot|  
|**schéma d’agrégation uniquement**|**0x01**|**0x01**|  
|**schéma de Func uniquement**|**0x01**|**0x01**|  
|**schéma de vue indexée uniquement**|**0x01**|**0x01**|  
|**logbased de vue indexée**|**0x30F3**|**0x3071**|  
|**la vue indexée base logarithmique manualboth**|**0x30F3**|**0x3071**|  
|**la vue indexée logbased manualfilter**|**0x30F3**|**0x3071**|  
|**la vue indexée logbased manualview**|**0x30F3**|**0x3071**|  
|**logbased**|**0x30F3**|**0x3071**|  
|**logbased manualfilter**|**0x30F3**|**0x3071**|  
|**logbased manualview**|**0x30F3**|**0x3071**|  
|**proc exec**|**0x01**|**0x01**|  
|**proc schéma uniquement**|**0x01**|**0x01**|  
|**serializable proc exec**|**0x01**|**0x01**|  
|**afficher le schéma uniquement**|**0x01**|**0x01**|  
  
> [!NOTE]
>  Si une publication est activée en file d’attente de la mise à jour, un *schema_option* valeur **0 x 80** est ajouté à la valeur par défaut indiquée dans le tableau. La valeur par défaut *schema_option* pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publication est **0x050D3**.  
  
## <a name="valid-schema-options"></a>Options de schéma valides  
 Ce tableau décrit les valeurs autorisées de *schema_option* basé sur le type de réplication (dans la partie supérieure) et le type d’article (dans la première colonne).  
  
|Type de l'article|Type de réplication||  
|------------------|----------------------|------|  
||Transactionnelle|Snapshot|  
|**logbased**|Toutes les options|Toutes les options mais **0 x 02**|  
|**logbased manualfilter**|Toutes les options|Toutes les options mais **0 x 02**|  
|**logbased manualview**|Toutes les options|Toutes les options mais **0 x 02**|  
|**logbased de vue indexée**|Toutes les options|Toutes les options mais **0 x 02**|  
|**la vue indexée logbased manualfilter**|Toutes les options|Toutes les options mais **0 x 02**|  
|**la vue indexée logbased manualview**|Toutes les options|Toutes les options mais **0 x 02**|  
|**la vue indexée base logarithmique manualboth**|Toutes les options|Toutes les options mais **0 x 02**|  
|**proc exec**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|  
|**serializable proc exec**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|  
|**proc schéma uniquement**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|  
|**afficher le schéma uniquement**|**0 x 01**, **0x010**, **0x020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0x800000**,  **0x2000000**, **0 x 8000000**, **0 x 40000000**, et **0 x 80000000**|**0 x 01**, **0x010**, **0x020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0x800000**,  **0x2000000**, **0 x 8000000**, **0 x 40000000**, et **0 x 80000000**|  
|**schéma de Func uniquement**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0x800000**, **0x2000000**, **0 x 8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, et **0 x 80000000**|  
|**schéma de vue indexée uniquement**|**0 x 01**, **0x010**, **0x020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0x800000**,  **0x2000000**, **0 x 8000000**, **0 x 40000000**, et **0 x 80000000**|**0 x 01**, **0x010**, **0x020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0x800000**,  **0x2000000**, **0 x 8000000**, **0 x 40000000**, et **0 x 80000000**|  
  
> [!NOTE]
>  Pour les publications avec mise à jour en file d’attente, le *schema_option* les valeurs de **0 x 8000** et **0 x 80** doit être activé. La prise en charge *schema_option* des valeurs non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publications sont : **0 x 01**, **0 x 02**, **0 x 10**, **0 x 40**, **0 x 80**, **0 x 1000**,  **0 x 4000** et **0 x 8000**.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-addarticle-transact-sql_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addarticle**.  
  
## <a name="see-also"></a>Voir aussi  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
