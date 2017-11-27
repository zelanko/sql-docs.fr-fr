---
title: "SAUVEGARDE de la base de données (Parallel Data Warehouse) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c8d465-b36b-4727-b9f3-368e98677c64
caps.latest.revision: "11"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ced03c90d0f30a1e8749d09f00d293bdee53b06e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="backup-database-parallel-data-warehouse"></a>SAUVEGARDE de la base de données (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Crée une sauvegarde d’un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] de base de données et stocke la sauvegarde de l’application dans un emplacement spécifié par l’utilisateur de réseau. Utilisez cette instruction avec [restaurer la base de données &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/restore-database-parallel-data-warehouse.md) pour la récupération d’urgence, ou copier une base de données à partir d’un équipement à un autre.  
  
 **Avant de commencer**, consultez « Acquérir et configuration d’un serveur de sauvegarde » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Il existe deux types de sauvegardes dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. A *sauvegarde complète de base de données* est une sauvegarde de l’intégralité d’un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] base de données. A *sauvegarde différentielle de base de données* inclut uniquement les modifications apportées depuis la dernière sauvegarde complète. Une sauvegarde de base de données utilisateur inclut la base de données et les rôles de base de données. Une sauvegarde de la base de données master comprend des connexions.  
  
 Pour plus d’informations sur [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] les sauvegardes de base de données, consultez « Sauvegarde et restauration » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      Create a full backup of a user database or the master database.  
BACKUP DATABASE database_name  
    TO DISK = '\\UNC_path\backup_directory'  
    [ WITH [ ( ]  <with_options> [ ,...n ]  [ ) ] ]  
[;]  
  
Create a differential backup of a user database.  
BACKUP DATABASE database_name  
    TO DISK = '\\UNC_path\backup_directory'  
    WITH [ ( ] DIFFERENTIAL   
    [ , <with_options> [ ,...n ] [ ) ]  
[;]  
  
<with_options> ::=  
    DESCRIPTION = 'text'  
    | NAME = 'backup_name'  
  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Le nom de la base de données sur lequel créer une sauvegarde. La base de données peut être la base de données master ou une base de données utilisateur.  
  
 SUR le disque = '\\\\*UNC_path*\\*Répertoire_Sauvegarde*'  
 Le chemin d’accès réseau et le répertoire dans lequel [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] écrira les fichiers de sauvegarde. Par exemple, «\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup ».  
  
-   Le chemin d’accès pour le nom du répertoire de sauvegarde doit déjà exister et doit être spécifiée comme chemin d’accès UNC universal qualifié complet.  
  
-   Le répertoire de sauvegarde, *Répertoire_Sauvegarde*, ne doit pas exister avant d’exécuter la commande de sauvegarde. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]crée le répertoire de sauvegarde.  
  
-   Le chemin d’accès au répertoire de sauvegarde ne peut pas être un chemin d’accès local et il ne peut pas être un emplacement sur n’importe quel le [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nœuds de l’appliance.  
  
-   La longueur maximale du chemin d’accès UNC et du nom du répertoire de sauvegarde est de 200 caractères.  
  
-   Le serveur ou l’hôte doit être spécifié en tant qu’une adresse IP.  Vous ne pouvez pas spécifier il comme nom d’hôte ou serveur.  
  
 DESCRIPTION = **'***texte***'**  
 Spécifie une description textuelle de la sauvegarde. La longueur maximale du texte est de 255 caractères.  
  
 La description est stockée dans les métadonnées et s’affichera lorsque l’en-tête de sauvegarde est restaurée avec RESTORE HEADERONLY.  
  
 NOM = **'***sauvegarde _ordinateur***'**  
 Spécifie le nom de la sauvegarde. Le nom de la sauvegarde peut être différent du nom de la base de données.  
  
-   Les noms peuvent contenir jusqu'à 128 caractères.  
  
-   Ne peut pas inclure un chemin d’accès.  
  
-   Doit commencer par une lettre ou un numéro de caractère ou un trait de soulignement (_). Les caractères spéciaux autorisés sont le trait de soulignement (\_), trait d’union (-) ou espace (). Noms de sauvegarde ne peut pas se terminer par un espace.  
  
-   L’instruction échoue si *nom_sauvegarde* existe déjà dans l’emplacement spécifié.  
  
 Ce nom est stocké dans les métadonnées et s’affichera lorsque l’en-tête de sauvegarde est restaurée avec RESTORE HEADERONLY.  
  
 DIFFERENTIAL  
 Spécifie l’exécution d’une sauvegarde différentielle de base de données utilisateur. Si omis, la valeur par défaut est une sauvegarde de base de données complète. Le nom de la sauvegarde différentielle n’a pas besoin de correspondre au nom de la sauvegarde complète. Pour le suivi de la sauvegarde différentielle et sa sauvegarde complète correspondante, envisagez d’utiliser le même nom avec « complet » ou « diff » ajouté.  
  
 Exemple :  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerFull';`  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerDiff' WITH DIFFERENTIAL;`  
  
## <a name="permissions"></a>Permissions  
 Requiert le **BACKUP DATABASE** autorisation ou l’appartenance dans le **db_backupoperator** rôle de base de données fixe. La base de données master ne peut pas être sauvegardée des mais par un utilisateur standard qui a été ajouté à la **db_backupoperator** rôle de base de données fixe. La base de données master peut uniquement être sauvegardée par **sa**, l’administrateur de l’ensemble fibre optique, ou les membres de la **sysadmin** rôle serveur fixe.  
  
 Nécessite un compte Windows qui a l’autorisation d’accès, créer et écrire dans le répertoire de sauvegarde. Vous devez également stocker le nom de compte Windows et le mot de passe dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Pour ajouter ces informations d’identification de réseau à [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le [sp_pdw_add_network_credentials &#40; Entrepôt de données SQL &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) procédure stockée.  
  
 Pour plus d’informations sur la gestion des informations d’identification dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], consultez la [sécurité](#Security) section.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Erreurs de base de données de sauvegarde dans les conditions suivantes :  
  
-   Autorisations de l’utilisateur ne sont pas suffisantes pour effectuer une sauvegarde.  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]n’a pas les autorisations appropriées à l’emplacement réseau où la sauvegarde sera stockée.  
  
-   La base de données n’existe pas.  
  
-   Le répertoire cible existe déjà sur le partage réseau.  
  
-   Le partage de réseau cible n’est pas disponible.  
  
-   Le partage de réseau cible n’a pas suffisamment d’espace pour la sauvegarde. La commande de sauvegarde de la base de données ne respecte pas la présence d’un espace disque suffisant avant de lancer la sauvegarde, ce qui permet de générer une erreur d’espace disque lors de la sauvegarde de la base de données en cours d’exécution. En cas d’espace disque insuffisant, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] annule la commande de sauvegarde de base de données. Pour réduire la taille de votre base de données, exécutez [DBCC SHRINKLOG (entrepôt de données SQL Azure)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md)  
  
-   Tentative de démarrer une sauvegarde dans une transaction.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Avant d’effectuer une sauvegarde de base de données, utilisez [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) pour réduire la taille de votre base de données. 
 
 A [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] sauvegarde est stockée comme un ensemble de plusieurs fichiers dans le même répertoire.  
  
 Généralement, une sauvegarde différentielle prend moins de temps qu’une sauvegarde complète et peut être effectuée plus souvent. Quand plusieurs sauvegardes différentielles sont basées sur la même sauvegarde complète, chaque sauvegarde différentielle inclut toutes les modifications dans la dernière sauvegarde différentielle.  
  
 Si vous annulez une commande BACKUP, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] supprimera le répertoire cible et tous les fichiers créés pour la sauvegarde. Si [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] perd la connectivité réseau au partage, ne peut pas effectuer la restauration.  
  
 Sauvegardes complètes et différentielles sont stockés dans des répertoires distincts. Conventions d’affectation de noms ne sont pas appliquées pour spécifier qu’une sauvegarde complète et une sauvegarde différentielle appartiennent ensemble. Vous pouvez le suivre via vos propres conventions d’affectation de noms. Vous pouvez également suivre cela à l’aide de l’option avec la DESCRIPTION pour ajouter une description, puis à l’aide de l’instruction RESTORE HEADERONLY pour récupérer la description.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Vous ne pouvez pas effectuer une sauvegarde différentielle de la base de données master. Uniquement les sauvegardes complètes de la base de données master sont pris en charge.  
  
 Les fichiers de sauvegarde sont stockés dans un format approprié uniquement pour la restauration de la sauvegarde à un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] matériel à l’aide de le [restaurer la base de données &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/restore-database-parallel-data-warehouse.md) instruction.  
  
 La sauvegarde avec l’instruction de sauvegarde de la base de données ne peut pas être utilisée pour transférer des données ou l’utilisateur des informations vers SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données. Pour cette fonctionnalité, vous pouvez utiliser la fonctionnalité de copie de la table distante. Pour plus d’informations, consultez « Copie de la Table distante » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologie pour sauvegarder et restaurer des bases de données de sauvegarde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]options de sauvegarde sont préconfigurées pour utiliser la compression de la sauvegarde. Impossible de définir les options de sauvegarde telles que la compression, somme de contrôle, taille de bloc et nombre de tampons.  
  
 Qu’une sauvegarde de base de données ou de restauration permettre s’exécuter sur le dispositif à un moment donné. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]file d’attente des commandes backup ou restore jusqu'à ce que la sauvegarde en cours ou la commande de restauration est terminée.  
  
 L’application cible pour la restauration de la sauvegarde doit avoir au moins autant de nœuds de calcul que l’application source. La cible peut avoir plusieurs nœuds de calcul à l’application source, mais ne peut pas avoir moins de nœuds de calcul.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ne pas effectuer le suivi de l’emplacement et les noms des sauvegardes dans la mesure où les sauvegardes sont stockées hors tension l’appliance.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]effectue le suivi la réussite ou l’échec des sauvegardes de base de données.  
  
 Une sauvegarde différentielle est uniquement autorisée si la dernière sauvegarde complète est terminée avec succès. Par exemple, supposons que le lundi, vous créez une sauvegarde complète de la base de données de ventes et la sauvegarde se termine avec succès. Mardi, vous créez une sauvegarde complète de la base de données de ventes, puis il échoue. Après cela, vous ne peut pas ensuite créer une sauvegarde différentielle est basée sur la sauvegarde complète de lundi. Vous devez d’abord créer une sauvegarde complète avant de créer une sauvegarde différentielle.  
  
## <a name="metadata"></a>Métadonnées  
 Ces vues de gestion dynamique contiennent des informations sur tous les sauvegarder, restaurer et opérations de chargement. Les informations sont conservées entre les redémarrages du système.  
  
-   [Sys.pdw_loader_backup_runs &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [Sys.pdw_loader_backup_run_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
-   [Sys.pdw_loader_run_stages &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md)  
  
## <a name="performance"></a>Performance  
 Pour effectuer une sauvegarde, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] première sauvegarde pour les métadonnées, puis effectue une sauvegarde en parallèle de la base de données stockées sur les nœuds de calcul. Dans le répertoire de sauvegarde, les données sont copiées directement à partir de chaque nœud de calcul. Pour obtenir de meilleures performances pour le déplacement des données à partir des nœuds de calcul dans le répertoire de sauvegarde, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] contrôle le nombre de nœuds de calcul qui copie des données simultanément.  
  
## <a name="locking"></a>Verrouillage  
 Applique un verrou de ExclusiveUpdate sur l’objet de base de données.  
  
##  <a name="Security"></a> Sécurité  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]les sauvegardes ne sont pas stockés sur le matériel. Par conséquent, votre équipe informatique est chargé de gérer tous les aspects de la sécurité de la sauvegarde. Par exemple, cela inclut la gestion de la sécurité des données de sauvegarde, la sécurité du serveur utilisé pour stocker les sauvegardes et la sécurité de l’infrastructure réseau qui connecte le serveur de sauvegarde à la [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] appliance.  
  
 **Gérer les informations d’identification réseau**  
  
 Accès réseau au répertoire de sauvegarde est basé sur la sécurité de partage de fichiers de Windows standard. Avant d’effectuer une sauvegarde, vous devez créer ou désigner un compte Windows qui sera utilisé pour l’authentification [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] au répertoire de sauvegarde. Ce compte windows doit avoir l’autorisation d’accès, de créer et d’écrire dans le répertoire de sauvegarde.  
  
> [!IMPORTANT]  
>  Pour réduire les risques de sécurité à vos données, il est conseillé que vous désignez un compte Windows uniquement à des fins de sauvegarde et les opérations de restauration. Autoriser ce compte disposent des autorisations à l’emplacement de sauvegarde et nulle part ailleurs.  
  
 Vous avez besoin de stocker le nom d’utilisateur et un mot de passe dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] en exécutant la [sp_pdw_add_network_credentials &#40; Entrepôt de données SQL &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) procédure stockée. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]utilise le Gestionnaire d’informations d’identification Windows pour stocker et de chiffrer des noms d’utilisateur et mots de passe sur le nœud de contrôle et les nœuds de calcul. Les informations d’identification ne sont pas sauvegardées avec la commande de sauvegarde de base de données.  
  
 Pour supprimer les informations d’identification de réseau à partir de [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], consultez [sp_pdw_remove_network_credentials &#40; Entrepôt de données SQL &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
 Pour répertorier toutes les informations d’identification réseau stockées dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le [sys.dm_pdw_network_credentials &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) vue de gestion dynamique.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-add-network-credentials-for-the-backup-location"></a>A. Ajouter des informations d’identification réseau pour l’emplacement de sauvegarde  
 Pour créer une sauvegarde, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] doit avoir l’autorisation de lecture/écriture au répertoire de sauvegarde. L’exemple suivant montre comment ajouter les informations d’identification pour un utilisateur. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]sera stocker ces informations d’identification à utiliser pour la sauvegarde et les opérations de restauration.  
  
> [!IMPORTANT]  
>  Pour des raisons de sécurité, nous vous recommandons de créer un compte de domaine uniquement dans le but de sauvegardes.  
  
```  
EXEC sp_pdw_add_network_credentials 'xxx.xxx.xxx.xxx', 'domain1\backupuser', '*****';  
```  
  
### <a name="b-remove-network-credentials-for-the-backup-location"></a>B. Supprimer les informations d’identification réseau pour l’emplacement de sauvegarde  
 L’exemple suivant montre comment supprimer les informations d’identification pour un utilisateur de domaine à partir de [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
```  
EXEC sp_pdw_remove_network_credentials 'xxx.xxx.xxx.xxx';  
```  
  
### <a name="c-create-a-full-backup-of-a-user-database"></a>C. Créer une sauvegarde complète de base de données utilisateur  
 L’exemple suivant crée une sauvegarde complète de la base de données utilisateur de factures. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]crée le répertoire Invoices2013 et enregistre les fichiers de sauvegarde à la \\\10.192.63.147\backups\yearly\Invoices2013Full active.  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="d-create-a-differential-backup-of-a-user-database"></a>D. Créer une sauvegarde différentielle de base de données utilisateur  
 L’exemple suivant crée une sauvegarde différentielle, qui inclut toutes les modifications apportées depuis la dernière sauvegarde complète de la base de données de factures. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]crée le \\Active \xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff auquel il stocke les fichiers. La description « factures 2013 la sauvegarde différentielle » sera stockée avec les informations d’en-tête pour la sauvegarde.  
  
 La sauvegarde différentielle ne s’exécute correctement si la dernière sauvegarde complète de factures a réussi.  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH DIFFERENTIAL,   
    DESCRIPTION = 'Invoices 2013 differential backup';  
```  
  
### <a name="e-create-a-full-backup-of-the-master-database"></a>E. Créer une sauvegarde complète de la base de données master  
 L’exemple suivant crée une sauvegarde complète de la base de données master et les stocke dans le répertoire '\\\10.192.63.147\backups\2013\daily\20130722\master'.  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master';  
```  
  
### <a name="f-create-a-backup-of-appliance-login-information"></a>F. Créer une sauvegarde des informations de connexion d’application.  
 La base de données master stocke les informations de connexion de matériel. Pour sauvegarder les informations de connexion d’application, vous devez le maître de sauvegarde.  
  
 L’exemple suivant crée une sauvegarde complète de la base de données master.  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master'  
WITH (   
    DESCRIPTION = 'Master Backup 20130722',  
    NAME = 'login-backup'  
)  
;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [RESTAURER la base de données &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
  
