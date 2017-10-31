---
title: "MODIFIER le fichier de base de données et les Options de groupe de fichiers (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ADD FILE
- ADD_FILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting files
- removing files
- deleting filegroups
- file modifications [SQL Server]
- databases [SQL Server], size
- relocating files
- databases [SQL Server], modifying
- file additions [SQL Server], ALTER DATABASE
- file moving [SQL Server]
- default filegroups
- ALTER DATABASE statement, files and filegroups
- initializing files [SQL Server]
- database files [SQL Server]
- moving files
- filegroups [SQL Server], deleting
- adding filegroups
- adding files
- database filegroups [SQL Server]
- adding log files
- modifying files
- filegroups [SQL Server], adding
- file initialization [SQL Server]
- files [SQL Server], deleting
- files [SQL Server], adding
- databases [SQL Server], moving
ms.assetid: 1f635762-f7aa-4241-9b7a-b51b22292b07
caps.latest.revision: 61
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fdd1f2aaab4e4aeeced6eb069255adba5b333abf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-file-and-filegroup-options"></a>MODIFIER les Options de groupe de fichiers et de la base de données (Transact-SQL) 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les fichiers et groupes de fichiers associés à la base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ajoute ou supprime des fichiers et des groupes de fichiers d'une base de données et modifie ses attributs ou ses fichiers et groupes de fichiers. Pour les autres options ALTER DATABASE, consultez [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER DATABASE database_name   
{  
    <add_or_modify_files>  
  | <add_or_modify_filegroups>  
}  
[;]  
  
<add_or_modify_files>::=  
{  
    ADD FILE <filespec> [ ,...n ]   
        [ TO FILEGROUP { filegroup_name } ]  
  | ADD LOG FILE <filespec> [ ,...n ]   
  | REMOVE FILE logical_file_name   
  | MODIFY FILE <filespec>  
}  
  
<filespec>::=   
(  
    NAME = logical_file_name    
    [ , NEWNAME = new_logical_name ]   
    [ , FILENAME = {'os_file_name' | 'filestream_path' | 'memory_optimized_data_path' } ]   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB| % ] ]   
    [ , OFFLINE ]  
)   
  
<add_or_modify_filegroups>::=  
{  
    | ADD FILEGROUP filegroup_name   
        [ CONTAINS FILESTREAM | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    | REMOVE FILEGROUP filegroup_name   
    | MODIFY FILEGROUP filegroup_name  
        { <filegroup_updatability_option>  
        | DEFAULT  
        | NAME = new_filegroup_name   
        | { AUTOGROW_SINGLE_FILE | AUTOGROW_ALL_FILES }  
        }  
}  
<filegroup_updatability_option>::=  
{  
    { READONLY | READWRITE }   
    | { READ_ONLY | READ_WRITE }  
}  
  
```  
  
## <a name="arguments"></a>Arguments  
**\<add_or_modify_files > :: =**
  
 Spécifie le fichier à ajouter, supprimer ou modifier.  
  
 *database_name*  
 Nom de la base de données à modifier.  
  
 ADD FILE  
 Ajoute un fichier à la base de données.  
  
 POUR le groupe de fichiers { *filegroup_name* }  
 Précise le groupe de fichiers auquel le fichier spécifié doit être ajouté. Pour afficher les groupes de fichiers et de groupe de fichiers auquel est la valeur par défaut en cours, utilisez la [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md) affichage catalogue.  
  
 ADD LOG FILE  
 Ajoute un fichier journal à la base de données spécifiée.  
  
 SUPPRIMER le fichier *nom_fichier_logique*  
 Supprime la description du fichier logique d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et supprime le fichier physique. Le fichier ne peut pas être supprimé s'il n'est pas vide.  
  
 *nom_fichier_logique*  
 Nom logique utilisé pour référencer le fichier dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!WARNING]  
>  Suppression d’un fichier de base de données qui a FILE_SNAPSHOT les sauvegardes associées à elle réussira, mais toutes les captures instantanées associées ne seront pas supprimées pour éviter l’invalidation de sauvegardes qui fait référence au fichier de base de données. Le fichier sera tronqué, mais n’est pas supprimé physiquement afin de conserver les sauvegardes FILE_SNAPSHOT. Pour plus d’informations, consultez [Sauvegarde et restauration SQL Server avec le service de stockage d’objets blob Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). **S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
 MODIFY FILE  
 Spécifie le fichier à modifier. Seul \<filespec > propriété peut être modifiée à la fois. NOM doit toujours être spécifié dans le \<filespec > pour identifier le fichier à modifier. Si vous définissez l'option SIZE, la nouvelle taille doit être supérieure à la taille actuelle du fichier.  
  
 Pour modifier le nom logique d'un fichier de données ou d'un fichier journal, spécifiez le nom logique du fichier à renommer dans la clause `NAME` et indiquez le nouveau nom logique à appliquer dans la clause `NEWNAME`. Exemple :  
  
```  
MODIFY FILE ( NAME = logical_file_name, NEWNAME = new_logical_name )   
```  
  
 Pour déplacer un fichier de données ou un fichier journal vers un nouvel emplacement, spécifiez le nom de fichier logique actuel dans la clause `NAME` et les nouveaux chemin d'accès et nom de fichier de système d'exploitation dans la clause `FILENAME`. Exemple :  
  
```  
MODIFY FILE ( NAME = logical_file_name, FILENAME = ' new_path/os_file_name ' )  
```  
  
 Lorsque vous déplacez un catalogue de texte intégral, spécifiez uniquement le nouveau fichier dans la clause FILENAME. N'indiquez pas le nom de fichier du système d'exploitation.  
  
 Pour plus d’informations, consultez [déplacer les fichiers de base de données](../../relational-databases/databases/move-database-files.md).  
  
 Pour un groupe de fichiers FILESTREAM, NAME peut être modifié en ligne. FILENAME peut être modifié en ligne ; toutefois, la modification n'entre pas en vigueur tant que le conteneur n'a pas été déplacé physiquement et le serveur arrêté puis redémarré.  
  
 Vous pouvez définir un fichier FILESTREAM sur OFFLINE. Lorsqu'un fichier FILESTREAM est hors connexion, son groupe de fichiers parent est marqué en interne comme hors connexion ; par conséquent, tout accès aux données FILESTREAM dans ce groupe de fichiers échoue.  
  
> [!NOTE]  
>  \<add_or_modify_files > options ne sont pas disponibles dans une base de données de contenu.
  
 **\<filespec > :: =**  
  
 Contrôle les propriétés des fichiers.  
  
 NOM *nom_fichier_logique*  
 Spécifie le nom logique du fichier.  
  
 *nom_fichier_logique*  
 Nom logique utilisé pour référencer le fichier dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 NEWNAME *new_logical_file_name*  
 Spécifie un nouveau nom logique pour le fichier.  
  
 *new_logical_file_name*  
 Nom remplaçant le nom de fichier logique existant. Le nom doit être unique au sein de la base de données et respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md). Il peut s'agir d'une constante de type caractère ou Unicode, d'un identificateur régulier ou d'un identificateur délimité.  
  
 Nom de fichier { **'***nom_fichier_se***'** | **'***filestream_path***'** | **'***memory_optimized_data_path***'**}  
 Spécifie un nom de fichier du système d'exploitation (physique).  
  
 ' *nom_fichier_se* '  
 Pour un groupe de fichiers standard (ROWS), il s'agit du chemin d'accès et du nom de fichier utilisés par le système d'exploitation lorsque vous créez le fichier. Le fichier doit résider sur le serveur hébergeant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le chemin d'accès spécifié doit exister avant l'exécution de l'instruction ALTER DATABASE.  
  
 Les paramètres SIZE, MAXSIZE et FILEGROWTH ne peuvent pas être définis lorsqu'un chemin d'accès UNC est spécifié pour le fichier.  
  
> [!NOTE]  
>  Les bases de données système ne peuvent pas résider dans les répertoires partagés UNC.  
  
 Les fichiers de données ne doivent pas être placés sur des systèmes de fichiers compressés à moins qu'il ne s'agisse de fichiers secondaires en lecture seule ou que la base de données soit en lecture seule. Les fichiers journaux ne doivent jamais être placés sur des systèmes de fichiers compressés.  
  
 Si le fichier se trouve sur une partition brute, *nom_fichier_se* doit spécifier uniquement la lettre de lecteur d’une partition brute existante. Chaque partition brute ne peut contenir qu'un seul fichier.  
  
 **'** *filestream_path* **'**  
 Pour un groupe de fichiers FILESTREAM, FILENAME fait référence à un chemin d'accès où les données FILESTREAM seront stockées. Le chemin d'accès jusqu'au dernier dossier doit exister, et le dernier dossier ne doit pas exister. Par exemple, si vous spécifiez le chemin d'accès C:\MyFiles\MyFilestreamData, C:\MyFiles doit exister avant l'exécution d'ALTER DATABASE, mais le dossier MyFilestreamData ne doit pas exister.  
  
 Les propriétés SIZE et FILEGROWTH ne s'appliquent pas à un groupe de fichiers FILESTREAM.  
  
 **'** *memory_optimized_data_path* **'**  
 Pour un groupe de fichiers mémoire optimisé, FILENAME fait référence à un chemin d'accès où les données mémoire optimisées sont stockées. Le chemin d'accès jusqu'au dernier dossier doit exister, et le dernier dossier ne doit pas exister. Par exemple, si vous spécifiez le chemin d'accès C:\MyFiles\MyData, C:\MyFiles doit exister avant l'exécution d'ALTER DATABASE, mais le dossier MyData ne doit pas exister.  
  
 Le groupe de fichiers et le fichier (`<filespec>`) doivent être créés dans la même instruction.  
  
 Les propriétés SIZE, MAXSIZE et FILEGROWTH ne s'appliquent pas à un groupe de fichiers mémoire optimisé.  
  
 TAILLE *taille*  
 Spécifie la taille du fichier. SIZE ne s'applique pas aux groupes de fichiers FILESTREAM.  
  
 *taille*  
 Est la taille du fichier.  
  
 Lorsque spécifié avec ADD FILE, *taille* est la taille initiale du fichier. Lorsque spécifiée avec MODIFY FILE, *taille* est la nouvelle taille pour le fichier et doit être supérieure à la taille du fichier.  
  
 Lorsque *taille* n’est pas fourni pour le fichier primaire, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise la taille du fichier primaire de la **modèle** base de données. Quand un fichier journal ou un fichier de données secondaire est spécifié mais *taille* n’est pas spécifié pour le fichier, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] rend le fichier de 1 Mo.  
  
 Les indications Ko, Mo, Go et To peuvent être utilisées pour indiquer qu'il s'agit de kilo-octets, mégaoctets, gigaoctets ou téraoctets. La valeur par défaut est Mo. Précisez un nombre entier sans aucune décimale. Pour spécifier une fraction d'un mégaoctet, convertissez la valeur en kilo-octet en multipliant le nombre par 1024. Par exemple, spécifiez 1536 Ko au lieu de 1,5 MB (1,5 x 1024 = 1536).  
  
 MAXSIZE { *max_size*| ILLIMITÉ}  
 Spécifie la taille de fichier maximale que peut atteindre le fichier.  
  
 *max_size*  
 Est la taille de fichier maximale. Les indications Ko, Mo, Go et To peuvent être utilisées pour indiquer qu'il s'agit de kilo-octets, mégaoctets, gigaoctets ou téraoctets. La valeur par défaut est Mo. Précisez un nombre entier sans aucune décimale. Si *max_size* n’est pas spécifié, la taille du fichier augmente jusqu'à ce que le disque est plein.  
  
 UNLIMITED  
 Précise que la taille du fichier peut croître jusqu'à ce que le disque soit saturé. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un fichier journal spécifié avec une croissance illimitée a une taille maximale de 2 To et un fichier de données une taille maximale de 16 To. Aucune taille maximale n'est définie lorsque cette option est spécifiée pour un conteneur FILESTREAM. Il continue à grandir jusqu'à ce que le disque soit saturé.  
  
 FILEGROWTH *growth_increment*  
 Spécifie l'incrément de croissance automatique du fichier. Le paramètre FILEGROWTH d'un fichier ne peut dépasser le paramètre MAXSIZE. FILEGROWTH ne s'applique pas aux groupes de fichiers FILESTREAM.  
  
 *growth_increment*  
 Représente la quantité d’espace ajoutée au fichier chaque fois qu’un espace supplémentaire est requis.  
  
 La valeur peut être exprimée en Mo, Ko, Go, To ou pourcentage (%). Si un nombre est mentionné sans spécifier Mo, Ko ou %, la valeur par défaut est Mo. Lorsque % est spécifié, la taille de l'incrément de croissance est le pourcentage choisi de la taille du fichier au moment où l'incrémentation a lieu. La taille spécifiée est arrondie à la valeur multiple de 64 Ko la plus proche.  
  
 Une valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé.  
  
 Si la croissance du fichier n’est pas spécifié, les valeurs par défaut sont :  
  
|Version|Valeurs par défaut|  
|-------------|--------------------|  
|Début[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|Données de 64 Mo. Les fichiers journaux 64 Mo.|  
|Début[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Données de 1 Mo. Fichiers journaux de 10 %.|  
|Versions antérieures à[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Données de 10 %. Fichiers journaux de 10 %.|  
  
 OFFLINE  
 Place le fichier en mode hors connexion et rend tous les objets du groupe de fichiers inaccessibles.  
  
> [!CAUTION]  
>  Utilisez cette option uniquement lorsque le fichier est endommagé et peut être restauré. Un fichier configuré avec l'option OFFLINE ne peut être remis en ligne qu'en le restaurant à partir d'une sauvegarde. Pour plus d’informations sur la restauration d’un fichier unique, consultez [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).  
  
> [!NOTE]  
>  \<spécification de fichier > options ne sont pas disponibles dans une base de données de contenu.  
  
 **\<add_or_modify_filegroups > :: =**  
  
 Ajoute, modifie ou supprime un groupe de fichiers à partir de la base de données.  
  
 Ajouter le groupe de fichiers *filegroup_name*  
 Ajoute un groupe de fichiers à la base de données.  
  
 CONTAINS FILESTREAM  
 Spécifie que le groupe de fichiers stocke des objets BLOB (binary large objects) FILESTREAM dans le système de fichiers.  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie que le groupe de fichiers stocke des données mémoire optimisées dans le système de fichiers. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). Un seul groupe de fichiers MEMORY_OPTIMIZED_DATA est autorisé par base de données. Pour créer des tables mémoire optimisées, le groupe de fichiers ne peut pas être vide. Il doit y avoir au moins un fichier. *FILEGROUP_NAME* fait référence à un chemin d’accès. Le chemin d'accès jusqu'au dernier dossier doit exister, et le dernier dossier ne doit pas exister.  
  
 L'exemple suivant crée un groupe de fichiers qui est ajouté à une base de données nommée xtp_db, puis ajoute un fichier dans le groupe de fichiers. Le groupe de fichiers stocke des données optimisées en mémoire.  
  
```  
ALTER DATABASE xtp_db ADD FILEGROUP xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA;  
GO  
ALTER DATABASE xtp_db ADD FILE (NAME='xtp_mod', FILENAME='d:\data\xtp_mod') TO FILEGROUP xtp_fg;  
```  
  
 SUPPRIMER le groupe de fichiers *filegroup_name*  
 Supprime un groupe de fichiers de la base de données. Le groupe de fichiers ne peut pas être supprimé s'il n'est pas vide. Commencez par supprimer tous les fichiers du groupe. Pour plus d’informations, consultez « Suppression du fichier *nom_fichier_logique*, » plus haut dans cette rubrique.  
  
> [!NOTE]  
>  Sauf dans le cas où le garbage collector FILESTREAM a supprimé tous les fichiers d'un conteneur FILESTREAM, l'opération ALTER DATABASE REMOVE FILE pour supprimer un conteneur FILESTREAM échoue et retourne une erreur. Consultez la section « Supprimer le conteneur FILESTREAM » dans les Notes dans la suite de cette rubrique.  
  
MODIFIER le groupe de fichiers *filegroup_name* { \<filegroup_updatability_option > | PAR DÉFAUT | NOM  **=**  *new_filegroup_name* } modifie le groupe de fichiers en définissant l’état READ_ONLY ou READ_WRITE, de rendre le groupe de fichiers du groupe de fichiers par défaut pour la base de données ou de la modification du nom de groupe de fichiers.  
  
 \<filegroup_updatability_option >  
 Définit la propriété read-only ou read/write du groupe de fichiers.  
  
 DEFAULT  
 Modifie le groupe de fichiers de base de données par défaut à *filegroup_name*. Dans une base de données, un seul groupe de fichiers peut être choisi comme groupe de fichiers par défaut. Pour plus d'informations, consultez [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md).  
  
 NOM = *new_filegroup_name*  
 Modifie le nom du groupe de fichiers pour le *new_filegroup_name*.  
  
 OPTIONS AUTOGROW_SINGLE_FILE  
**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Lorsqu’un fichier dans le groupe de fichiers est conforme au seuil de croissance automatique, seul ce fichier s’agrandit. Il s'agit du paramètre par défaut.  
  
 AUTOGROW_ALL_FILES  

**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Lorsqu’un fichier dans le groupe de fichiers est conforme au seuil de croissance automatique, tous les fichiers dans le groupe de fichiers augmente.  
  
 **\<filegroup_updatability_option > :: =**  
  
 Définit la propriété read-only ou read/write du groupe de fichiers.  
  
 READ_ONLY | READONLY  
 Précise que le groupe de fichiers est en mode lecture seule. La mise à jour des objets n'est pas autorisée. Le groupe de fichiers principal ne peut pas être en mode lecture seule. Pour modifier cet état, vous devez bénéficier d'un accès exclusif à la base de données. Pour plus d'informations, consultez la clause SINGLE_USER.  
  
 Étant donné qu'une base de données en lecture seule interdit la modification des données :  
  
-   La récupération automatique est ignorée au démarrage du système.  
  
-   Le compactage de la base de données est impossible.  
  
-   Tout verrouillage est impossible dans les bases de données en lecture seule, ce qui améliore les performances des requêtes.  
  
> [!NOTE]  
>  Le mot clé READONLY sera supprimée dans une future version de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser READONLY dans le développement de nouvelles applications et prévoyez de modifier celles qui utilisent actuellement READONLY. Utilisez à la place READ_ONLY.  
  
 READ_WRITE | READWRITE  
 Spécifie que le groupe a l'option READ_WRITE. Les objets du groupe de fichiers peuvent être mis à jour. Pour modifier cet état, vous devez bénéficier d'un accès exclusif à la base de données. Pour plus d'informations, consultez la clause SINGLE_USER.  
  
> [!NOTE]  
>  Le mot clé READWRITE sera supprimée dans une future version de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser READWRITE dans le développement de nouvelles applications et prévoyez de modifier celles qui utilisent actuellement READWRITE. Utilisez à la place READ_WRITE.  
  
 L’état de ces options peut être déterminé en examinant la **is_read_only** colonne dans la **sys.databases** affichage catalogue ou **mise à jour** propriété de la fonction DATABASEPROPERTYEX.  
  
## <a name="remarks"></a>Notes  
 Pour réduire la taille d’une base de données, utilisez [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
 Vous ne pouvez pas ajouter ou supprimer de fichier tant qu'une instruction BACKUP est en cours d'exécution.  
  
 Un maximum de 32 767 fichiers et 32 767 groupes de fichiers peut être spécifié pour chaque base de données.  
  
 Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, l'état d'un fichier de base de données (par exemple, en ligne ou hors connexion) est préservé indépendamment de l'état de la base de données. Pour plus d’informations, consultez [États des fichiers](../../relational-databases/databases/file-states.md). L'état des fichiers dans un groupe de fichiers détermine la disponibilité de tout le groupe de fichiers. Pour qu'un groupe de fichiers soit disponible, tous ses fichiers doivent être en ligne. Si un groupe de fichiers est hors connexion, toute tentative d'accès au groupe par une instruction SQL échoue avec une erreur. Lorsque vous créez des plans de requête pour les instructions SELECT, l'optimiseur de requête évite les index non cluster et les vues indexées qui résident dans les groupes de fichiers hors connexion. Cela permet aux instructions de s'exécuter correctement. Cependant, si le groupe de fichiers hors connexion contient le segment ou l'index cluster d'une table cible, les instructions SELECT échouent. De plus, toute instruction INSERT, UPDATE ou DELETE modifiant une table assortie d'un index dans un groupe de fichiers hors connexion ne peut être exécutée.  
  
## <a name="moving-files"></a>Déplacement de fichiers  
 Vous pouvez déplacer des données système ou définies par l'utilisateur ainsi que des fichiers journaux en spécifiant le nouvel emplacement dans FILENAME. Cela peut être utile dans les cas suivants :  
  
-   Récupération après défaillance. Par exemple, la base de données est en mode suspect ou arrêtée à cause d'une défaillance matérielle  
  
-   Déplacement prévu  
  
-   Déplacement en vue d’une maintenance de disque planifiée  
  
 Pour plus d’informations, consultez [déplacer les fichiers de base de données](../../relational-databases/databases/move-database-files.md).  
  
## <a name="initializing-files"></a>Initialisation des fichiers  
 Par défaut, les fichiers de données et journaux sont initialisés en remplissant les fichiers avec des zéros lorsque vous effectuez l'une des opérations suivantes :  
  
-   création d'une base de données ;  
  
-   ajout de fichiers à une base de données existante ;  
  
-   augmentation de la taille d'un fichier existant ;  
  
-   restauration d'une base de données ou d'un groupe de fichiers.  
  
 Les fichiers de données peuvent être initialisés de manière instantanée. Dès lors, l'exécution de ces opérations de fichiers est très rapide.  
  
## <a name="removing-a-filestream-container"></a>Suppression d'un conteneur FILESTREAM  
 Même si le conteneur FILESTREAM a peut-être été vidé à l'aide de l'opération DBCC SHRINKFILE, la base de données peut encore peut-être conserver des références aux fichiers supprimés pour des raisons de maintenance du système. [sp_filestream_force_garbage_collection &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md) s’exécutera le Garbage Collector FILESTREAM pour supprimer ces fichiers quand il est possible de le faire. Sauf dans le cas où le garbage collector FILESTREAM a supprimé tous les fichiers d'un conteneur FILESTREAM, l'opération ALTER DATABASEREMOVE FILE ne parviendra pas à supprimer un conteneur FILESTREAM et retournera une erreur. Le processus suivant est recommandé pour supprimer un conteneur FILESTREAM.  
  
1.  Exécutez [DBCC SHRINKFILE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) avec l’option EMPTYFILE pour déplacer le contenu actif de ce conteneur vers d’autres conteneurs.  
  
2.  Assurez-vous que les sauvegardes de journal ont été effectuées, en mode de récupération FULL ou BULK_LOGGED.  
  
3.  Assurez-vous que le travail du lecteur du journal de la réplication a été exécuté, le cas échéant.  
  
4.  Exécutez [sp_filestream_force_garbage_collection &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md) pour forcer le garbage collector pour supprimer tous les fichiers qui ne sont plus nécessaires dans ce conteneur.  
  
5.  Exécutez ALTER DATABASE avec l'option REMOVE FILE pour supprimer ce conteneur.  
  
6.  Répétez encore une fois les étapes 2 à 4 pour terminer le garbage collection.  
  
7.  Utilisez ALTER base de données...REMOVE FILE pour supprimer ce conteneur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-adding-a-file-to-a-database"></a>A. Ajout d'un fichier à une base de données  
 L'exemple suivant ajoute un fichier de données de 5 Mo à la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = Test1dat2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat2.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="b-adding-a-filegroup-with-two-files-to-a-database"></a>B. Ajout d'un groupe de deux fichiers à une base de données  
 L'exemple suivant crée le groupe de fichiers `Test1FG1` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] et ajoute deux fichiers de 5 Mo au groupe de fichiers.  
  
```  
USE master  
GO  
ALTER DATABASE AdventureWorks2012  
ADD FILEGROUP Test1FG1;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = test1dat3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat3.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1dat4,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat4.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
)  
TO FILEGROUP Test1FG1;  
GO  
  
```  
  
### <a name="c-adding-two-log-files-to-a-database"></a>C. Ajout de deux fichiers journaux à une base de données  
 L'exemple suivant ajoute deux fichiers journaux de 5 Mo à la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD LOG FILE   
(  
    NAME = test1log2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\test2log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1log3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\test3log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="d-removing-a-file-from-a-database"></a>D. Suppression d'un fichier d'une base de données  
 L'exemple suivant supprime l'un des fichiers ajoutés dans l'exemple B.  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4;  
GO  
  
```  
  
### <a name="e-modifying-a-file"></a>E. Modification d'un fichier  
L'exemple suivant augmente la taille de l'un des fichiers ajoutés dans l'exemple B.  
 L’instruction ALTER DATABASE avec la commande modifier le fichier peut uniquement agrandir une taille de fichier, si vous avez besoin réduire la taille du fichier vous devez donc utiliser DBCC SHRINKFILE.  
  
```  
USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO  
```

Cet exemple réduit la taille d’un fichier de données de 100 Mo et puis spécifie la taille de ce montant. 

```
USE AdventureWorks2012;
GO

DBCC SHRINKFILE (AdventureWorks2012_data, 100);
GO

USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO
```
 
  
### <a name="f-moving-a-file-to-a-new-location"></a>F. Déplacement d'un fichier vers un nouvel emplacement  
 L'exemple suivant déplace le fichier `Test1dat2` créé dans l'exemple A vers un nouveau répertoire.  
  
> [!NOTE]  
>  Vous devez déplacer physiquement le fichier vers le nouveau répertoire avant d'exécuter cet exemple. Après quoi, arrêtez et démarrez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou mettez la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] hors connexion (OFFLINE) puis remettez-la en ligne (ONLINE) pour implémenter la modification.  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
MODIFY FILE  
(  
    NAME = Test1dat2,  
    FILENAME = N'c:\t1dat2.ndf'  
);  
GO  
```  
  
### <a name="g-moving-tempdb-to-a-new-location"></a>G. Déplacement de tempdb vers un nouvel emplacement  
 L'exemple suivant déplace `tempdb` de son emplacement actuel vers un autre emplacement du disque. Étant donné que `tempdb` est recréée à chaque démarrage du service MSSQLSERVER, il n'est pas nécessaire de déplacer physiquement les fichiers de données et les fichiers journaux. Les fichiers sont créés lorsque le service est redémarré à l'étape 3. Tant que le service n'a pas été redémarré, `tempdb` continue à fonctionner dans son emplacement existant.  
  
1.  Déterminez les noms de fichier logique de la `tempdb` base de données et de leur emplacement actuel sur le disque.  
  
    ```  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    GO  
    ```  
  
2.  Modifiez l'emplacement de chaque fichier à l'aide de `ALTER DATABASE`.  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE  tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'E:\SQLData\templog.ldf');  
    GO  
    ```  
  
3.  Arrêtez et redémarrez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Vérifiez que la modification des fichiers a bien eu lieu.  
  
    ```  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    ```  
  
5.  Supprimez les fichiers empdb.mdf et templog.ldf de leur emplacement d'origine.  
  
### <a name="h-making-a-filegroup-the-default"></a>H. Configuration d'un groupe de fichiers comme groupe par défaut  
 L’exemple suivant montre la `Test1FG1` groupe de fichiers est créé dans l’exemple B le groupe de fichiers par défaut. Ensuite, le groupe de fichiers par défaut est reconfiguré en groupe de fichiers `PRIMARY`. Notez que `PRIMARY` doit être délimité par des crochets ou des guillemets.  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP Test1FG1 DEFAULT;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP [PRIMARY] DEFAULT;  
GO  
  
```  
  
### <a name="i-adding-a-filegroup-using-alter-database"></a>I. Ajout d'un groupe de fichiers à l'aide d'ALTER DATABASE  
 L'exemple de code suivant ajoute un `FILEGROUP` qui contient la clause `FILESTREAM` à la base de données `FileStreamPhotoDB`.  
  
```  
--Create and add a FILEGROUP that CONTAINS the FILESTREAM clause to  
--the FileStreamPhotoDB database.  
ALTER DATABASE FileStreamPhotoDB  
ADD FILEGROUP TodaysPhotoShoot  
CONTAINS FILESTREAM;  
GO  
  
--Add a file for storing database photos to FILEGROUP   
ALTER DATABASE FileStreamPhotoDB  
ADD FILE  
(  
    NAME= 'PhotoShoot1',  
    FILENAME = 'C:\Users\Administrator\Pictures\TodaysPhotoShoot.ndf'  
)  
TO FILEGROUP TodaysPhotoShoot;  
GO  
```      
        
### <a name="j-change-filegroup-so-that-when-a-file-in-the-filegroup-meets-the-autogrow-threshold-all-files-in-the-filegroup-grow"></a>J. Modifier le groupe de fichiers afin que lorsqu’un fichier dans le groupe de fichiers est conforme au seuil de croissance automatique, tous les fichiers dans le groupe de fichiers augmente
 L’exemple suivant génère le requis `ALTER DATABASE` instructions pour modifier les groupes de fichiers en lecture-écriture avec le `AUTOGROW_ALL_FILES` paramètre.  
  
```  
--Generate ALTER DATABASE ... MODIFY FILEGROUP statements  
--so that all read-write filegroups grow at the same time.  
SET NOCOUNT ON;

DROP TABLE IF EXISTS #tmpdbs
CREATE TABLE #tmpdbs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, isdone bit);

DROP TABLE IF EXISTS #tmpfgs
CREATE TABLE #tmpfgs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, fgname sysname, isdone bit);

INSERT INTO #tmpdbs ([dbid], [dbname], [isdone])
SELECT database_id, name, 0 FROM master.sys.databases (NOLOCK) WHERE is_read_only = 0 AND state = 0;

DECLARE @dbid int, @query VARCHAR(1000), @dbname sysname, @fgname sysname

WHILE (SELECT COUNT(id) FROM #tmpdbs WHERE isdone = 0) > 0
BEGIN
    SELECT TOP 1 @dbname = [dbname], @dbid = [dbid] FROM #tmpdbs WHERE isdone = 0

    SET @query = 'SELECT ' + CAST(@dbid AS NVARCHAR) + ', ''' + @dbname + ''', [name], 0 FROM [' + @dbname + '].sys.filegroups WHERE [type] = ''FG'' AND is_read_only = 0;'
    INSERT INTO #tmpfgs
    EXEC (@query)

    UPDATE #tmpdbs
    SET isdone = 1
    WHERE [dbid] = @dbid
END;

IF (SELECT COUNT(ID) FROM #tmpfgs) > 0
BEGIN
    WHILE (SELECT COUNT(id) FROM #tmpfgs WHERE isdone = 0) > 0
    BEGIN
        SELECT TOP 1 @dbname = [dbname], @dbid = [dbid], @fgname = fgname FROM #tmpfgs WHERE isdone = 0

        SET @query = 'ALTER DATABASE [' + @dbname + '] MODIFY FILEGROUP [' + @fgname + '] AUTOGROW_ALL_FILES;'

        PRINT @query

        UPDATE #tmpfgs
        SET isdone = 1
        WHERE [dbid] = @dbid AND fgname = @fgname
    END
END; 
GO  
```      
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [Sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [Sys.FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Objets binaires volumineux &#40;Objet BLOB&#41; Données &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)   
 [sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
  
  

