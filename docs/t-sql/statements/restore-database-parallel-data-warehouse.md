---
title: "RESTAURATION de base de données (Parallel Data Warehouse) | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d915bfc1-e392-4a3a-9d94-08682cf3c864
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 001813cf0e7d00e089046d8580108eb10ef4cba0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="restore-database-parallel-data-warehouse"></a>RESTAURER la base de données (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Restaure un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] base de données utilisateur à partir d’une sauvegarde de base de données à un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] appliance. La base de données est restaurée à partir d’une sauvegarde qui a été créée précédemment par le [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] [sauvegarde de base de données &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/backup-database-parallel-data-warehouse.md) commande. Utilisez la sauvegarde et de restauration des opérations pour créer un plan de récupération d’urgence, ou pour déplacer des bases de données à partir d’une application vers un autre.  
  
> [!NOTE]  
>  Restauration de master inclut la restauration des informations de connexion d’application. Pour restaurer master, utilisez le [restaurer la base de données master &#40; Transact-SQL &#41; ](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md) page dans le **Configuration Manager** outil. Un administrateur ayant accès au nœud de contrôle peut effectuer cette opération.  
  
 Pour plus d’informations sur [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] les sauvegardes de base de données, consultez « Sauvegarde et restauration » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      Restore the master database  
-- Use the Configuration Manager tool.  
  
Restore a full user database backup.  
RESTORE DATABASE database_name   
    FROM DISK = '\\UNC_path\full_backup_directory'  
[;]  
  
Restore a full user database backup and then a differential backup.  
RESTORE DATABASE database_name  
    FROM DISK = '\\UNC_path\differential_backup_directory'   
    WITH [ ( ] BASE = '\\UNC_path\full_backup_directory' [ ) ]   
[;]  
  
Restore header information for a full or differential user database backup.  
RESTORE HEADERONLY   
    FROM DISK = '\\UNC_path\backup_directory'  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 RESTAURER la base de données *nom_base_de_données*  
 Spécifie pour restaurer une base de données utilisateur à une base de données appelée *nom_base_de_données*. La base de données restaurée peut avoir un nom différent de la base de données source qui a été sauvegardée. *database_name* ne peut pas déjà exister en tant que base de données sur l’application de destination. Pour plus d’informations sur autorisées des noms de base de données, consultez « Règles d’affectation de noms d’objet » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Restauration d’une base de données utilisateur restaure une sauvegarde complète de la base de données et restaure ensuite éventuellement une sauvegarde différentielle à l’appliance. Restauration d’une base de données utilisateur inclut la restauration de base de données et les rôles de base de données.  
  
 À partir du disque = '\\\\*UNC_path*\\*Répertoire_Sauvegarde*'  
 Le chemin d’accès réseau et le répertoire à partir de laquelle [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] restaure les fichiers de sauvegarde. Par exemple, à partir du disque = '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup'.  
  
 *Répertoire_Sauvegarde*  
 Spécifie le nom d’un répertoire qui contient la sauvegarde complète ou différentielle. Par exemple, vous pouvez effectuer une opération RESTORE HEADERONLY sur une sauvegarde complète ou différentielle.  
  
 *full_backup_directory*  
 Spécifie le nom d’un répertoire qui contient la sauvegarde complète.  
  
 *differential_backup_directory*  
 Spécifie le nom du répertoire qui contient la sauvegarde différentielle.  
  
-   Le répertoire de sauvegarde et de chemin d’accès doit déjà exister et doit être spécifié comme chemin d’accès UNC universal qualifié complet.  
  
-   Le chemin d’accès au répertoire de sauvegarde ne peut pas être un chemin d’accès local et il ne peut pas être un emplacement sur n’importe quel le [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nœuds de l’appliance.  
  
-   La longueur maximale du chemin d’accès UNC et du nom du répertoire de sauvegarde est de 200 caractères.  
  
-   Le serveur ou l’hôte doit être spécifié en tant qu’une adresse IP.  
  
 RESTORE HEADERONLY  
 Spécifie pour retourner uniquement les informations d’en-tête pour la sauvegarde de base de données d’un utilisateur. Parmi les autres champs, l’en-tête inclut la description de la sauvegarde et le nom de la sauvegarde. Le nom de la sauvegarde n’a pas besoin être le même que le nom du répertoire où sont stockés les fichiers de sauvegarde.  
  
 Les résultats RESTORE HEADERONLY sont modélisées après le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] RESTORE HEADERONLY des résultats. Le résultat contient plus de 50 colonnes qui sont pas tous utilisés par [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Pour obtenir une description des colonnes dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des résultats RESTORE HEADERONLY, consultez [RESTORE HEADERONLY &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-headeronly-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Requiert le **CREATE ANY DATABASE** autorisation.  
  
 Nécessite un compte Windows qui a l’autorisation d’accéder à et lire à partir du répertoire de sauvegarde. Vous devez également stocker le nom de compte Windows et le mot de passe dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
1.  Pour vérifier les informations d’identification sont déjà, utilisez [sys.dm_pdw_network_credentials &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
2.  Pour ajouter ou mettre à jour les informations d’identification, utilisez [sp_pdw_add_network_credentials &#40; Entrepôt de données SQL &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
3.  Pour supprimer les informations d’identification à partir de [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez [sp_pdw_remove_network_credentials &#40; Entrepôt de données SQL &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
## <a name="error-handling"></a>Gestion des erreurs  
 La commande de restauration de la base de données provoque des erreurs dans les conditions suivantes :  
  
-   Le nom de la base de données à restaurer déjà existe sur l’appareil cible. Pour éviter ce problème, choisissez un nom de base de données unique, ou supprimer la base de données existante avant d’exécuter la restauration.  
  
-   Il existe un ensemble non valide de fichiers de sauvegarde dans le répertoire de sauvegarde.  
  
-   Les autorisations de connexion ne sont pas suffisantes pour restaurer une base de données.  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]n’a pas les autorisations appropriées à l’emplacement réseau où se trouvent les fichiers de sauvegarde.  
  
-   L’emplacement réseau pour le répertoire de sauvegarde n’existe pas ou n’est pas disponible.  
  
-   Il existe un espace disque insuffisant sur les nœuds de calcul ou d’un nœud de contrôle. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ne confirme pas que suffisamment d’espace disque existe sur l’appareil avant le lancement de la restauration. Par conséquent, il est possible de générer une erreur d’espace disque lors de l’exécution de l’instruction RESTORE DATABASE. En cas d’espace disque insuffisant, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] restaure la restauration.  
  
-   L’application cible dans lequel la base de données est restaurée a moins de nœuds de calcul à l’application de la source à partir de laquelle la base de données a été sauvegardée.  
  
-   La restauration de la base de données est tentée à partir d’une transaction.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]effectue le suivi de la réussite de la restauration de la base de données. Avant de restaurer une sauvegarde différentielle de base de données, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] vérifie la restauration de la base de données complète est terminée.  
  
 Après une restauration, la base de données utilisateur aura le niveau de compatibilité de base de données 120. Cela est vrai pour toutes les bases de données, quelle que soit leur niveau de compatibilité d’origine.  
  
 **Restauration vers un appareil avec un plus grand nombre de nœuds de calcul**  
Exécutez [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) après la restauration d’une base de données à partir d’un équipement plus petit au plus grand, car la redistribution augmentera le journal des transactions.  

Restauration d’une sauvegarde vers un appareil avec un plus grand nombre de nœuds de calcul s’agrandit la taille de la base de données alloué proportionnellement au nombre de nœuds de calcul.  
  
Par exemple, lorsque restauration 60 Go de base de données à partir d’un équipement de 2 nœuds (30 Go par nœud) à un matériel 6-nœud, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] crée une base de données 180 Go (6 nœuds avec 30 Go par nœud) sur le dispositif de 6 nœuds. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]initialement restaure la base de données à 2 nœuds correspondant à la configuration de la source, puis redistribue les données à tous les nœuds de 6.  
  
 Après la redistribution de chaque nœud de calcul contient moins de données réelles et davantage d’espace libre que chaque nœud de calcul sur l’appareil source plus petit. L’espace supplémentaire permet d’ajouter des données à la base de données. Si la taille de la base de données restaurée est plus grande que vous avez besoin, vous pouvez utiliser [ALTER DATABASE &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/alter-database-parallel-data-warehouse.md) pour réduire la taille des fichiers de base de données.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Pour obtenir ces limitations et restrictions, l’application source est l’application à partir de laquelle la sauvegarde de base de données a été créée, et l’application cible est l’application vers laquelle la base de données sera restaurée.  
  
 Restauration d’une base de données ne régénère pas automatiquement les statistiques.  
  
 Instruction qu’une seule de restaurer la base de données ou de sauvegarde de base de données peut être en cours d’exécution sur le matériel à un moment donné. Si plusieurs instructions de sauvegarde et de restauration sont envoyées simultanément, elle les placer dans une file d’attente, puis les traiter un à la fois.  
  
 Vous pouvez uniquement restaurer une sauvegarde de base de données à un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] équipement cible qui a le même nombre ou plusieurs nœuds de calcul à l’application source. L’appareil cible ne peut pas avoir moins de nœuds de calcul à l’application source.  
  
 Vous ne pouvez pas restaurer une sauvegarde qui a été créée sur un matériel qui possède un matériel de SQL Server 2012 PDW vers un appareil qui possède un matériel de SQL Server 2008 R2. Cela est vrai même si l’application a été achetée avec le matériel de PDW de SQL Server 2008 R2 et est en cours d’exécution des logiciels de SQL Server 2012 PDW.  
  
## <a name="locking"></a>Verrouillage  
 Accepte un verrou exclusif sur l’objet de base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-restore-examples"></a>A. Exemples de restauration simples  
 L’exemple suivant restaure une sauvegarde complète sur le `SalesInvoices2013` base de données. Les fichiers de sauvegarde sont stockés dans le \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full active. La base de données SalesInvoices2013 ne peut pas déjà exister sur l’appareil cible, ou cette commande échoue avec une erreur.  
  
```  
RESTORE DATABASE SalesInvoices2013  
FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="b-restore-a-full-and-differential-backup"></a>B. Restaurer une sauvegarde complète et différentielle  
 L’exemple suivant restaure un complet, puis une sauvegarde différentielle de la base de données SalesInvoices2013  
  
 La sauvegarde complète de la base de données est restaurée à partir de la sauvegarde complète qui est stockée dans le '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full' active. Si la restauration est terminée avec succès, la sauvegarde différentielle est restaurée dans la base de données SalesInvoices2013.  La sauvegarde différentielle est stockée dans le '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff' active.  
  
```  
RESTORE DATABASE SalesInvoices2013  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH BASE = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
  
```  
  
### <a name="c-restoring-the-backup-header"></a>C. Restauration de l’en-tête de sauvegarde  
 Cet exemple restaure les informations d’en-tête pour la sauvegarde de base de données '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'. Les résultats de la commande dans une ligne d’informations pour la sauvegarde Invoices2013Full.  
  
```  
RESTORE HEADERONLY  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
```  
  
 Vous pouvez utiliser les informations d’en-tête pour vérifier le contenu d’une sauvegarde, ou vérifiez que le matériel de restauration cible est compatible avec l’application de sauvegarde source avant de tenter de restaurer la sauvegarde.  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données de sauvegarde &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/backup-database-parallel-data-warehouse.md)  
  
  

