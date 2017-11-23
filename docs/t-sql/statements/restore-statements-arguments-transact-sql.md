---
title: Arguments de restauration (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/05/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- RESTORE statement, arguments
- RESTORE statement
ms.assetid: 4bfe5734-3003-4165-afd4-b1131ea26e2b
caps.latest.revision: "154"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 387e808d57395db8978611b311f54df441eabc91
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="restore-statements---arguments-transact-sql"></a>RESTORE, instructions - Arguments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique documente les arguments qui sont décrits dans la section « Syntaxe » de l'instruction RESTORE {DATABASE|LOG} et des instructions auxiliaires associées : RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY et RESTORE VERIFYONLY. La plupart des arguments sont pris en charge seulement par un sous-ensemble de ces six instructions. Cette prise en charge est précisée dans la description de chacun des arguments.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
 Pour la syntaxe, consultez les rubriques suivantes :  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
-   [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
-   [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)  
  
-   [RESTORE REWINDONLY &#40; Transact-SQL &#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)  
  
-   [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
## <a name="arguments"></a>Arguments  
 DATABASE  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Spécifie la base de données cible. Si une liste de fichiers et de groupes de fichiers est fournie, seuls ceux-là seront restaurés.  
  
 Pour une base de données en mode de récupération complète ou utilisant les journaux de transactions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite dans la plupart des cas une sauvegarde de la fin du journal, avant la restauration de la base de données. Restaurer une base de données sans effectuer une sauvegarde de la fin du journal au préalable entraîne une erreur, sauf si l'instruction RESTORE DATABASE contient la clause WITH REPLACE ou WITH STOPAT, qui doit spécifier une heure ou une transaction qui s'est produite après la fin de la sauvegarde des données. Pour plus d’informations sur les sauvegardes de la fin du journal, consultez [Sauvegardes de la fin du journal &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).  
  
 LOG  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Spécifie qu'une sauvegarde du journal des transactions doit être appliquée à cette base de données. Les journaux de transactions doivent être sollicités dans un ordre séquentiel. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vérifie le journal des transactions sauvegardé pour s'assurer que les transactions vont être chargées dans la base de données correcte et dans l'ordre adéquat. Pour appliquer plusieurs journaux de transactions, utilisez l'option NORECOVERY sur toutes les opérations de restauration sauf la dernière.  
  
> [!NOTE]  
>  En général, le dernier journal restauré est la sauvegarde de la fin du journal. A *sauvegarde de la fin du journal* est une sauvegarde du journal effectuée juste avant la restauration d’une base de données, généralement après un échec de la base de données. L'utilisation d'une sauvegarde de la fin du journal à partir d'une base de données probablement endommagée empêche la perte de travail en capturant le journal qui n'a pas encore été sauvegardé (la fin du journal). Pour plus d’informations, consultez [Sauvegardes de la fin du journal &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).  
  
 Pour plus d’informations, consultez [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
 { *nom_base_de_données* | **@***var_nom_base_de_données*}  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Base de données dans laquelle est restaurée la base complète ou le journal des transactions. Fourni comme variable (**@***var_nom_base_de_données*), ce nom peut être spécifié comme constante de chaîne (**@***var_nom_base_de_données* = *base de données*_*nom*) ou comme une variable de type chaîne de caractères, à l’exception de la **ntext** ou **texte** des types de données.  
  
 \<file_or_filegroup_or_page > [ **,**... *n* ]  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Spécifie le nom d'un fichier, d'un groupe de fichiers ou d'une page logique à inclure dans une instruction RESTORE DATABASE ou RESTORE LOG. Vous pouvez spécifier une liste de fichiers ou de groupes de fichiers.  
  
 Pour une base de données qui utilise le mode de récupération simple, les options FILE et FILEGROUP sont autorisées uniquement si les fichiers de la cible ou les groupes de fichiers sont en lecture seule, ou s’il s’agit d’une restauration partielle (ce qui entraîne un [groupe de fichiers défunt](../../relational-databases/backup-restore/remove-defunct-filegroups-sql-server.md)).  
  
 ?Pour une base de données utilisant le mode de restauration complète ou le mode de récupération utilisant les journaux de transactions, après l'utilisation de RESTORE DATABASE pour restaurer un ou plusieurs fichiers, groupes de fichiers, et/ou pages, en général, vous devez appliquer le journal des transactions aux fichiers contenant les données restaurées ; l'application du journal assure la cohérence de ces fichiers avec le reste de la base de données. Les exceptions sont les suivantes :  
  
-   Si les fichiers en cours de restauration étaient en lecture seule avant la dernière sauvegarde, puis un journal des transactions n’a pas à appliquer, et l’instruction RESTORE vous informe de cette situation.  
  
-   Si la sauvegarde contient le groupe de fichiers principal et qu'une restauration partielle est entreprise. Dans ce cas, le journal des restaurations n'est pas nécessaire car le journal est restauré automatiquement à partir du jeu de sauvegarde.  
  
FICHIER  **=**  { *nom_fichier_logique_dans_sauvegarde*| **@***logical_file_name_in_backup_var*}  
 Désigne un fichier à inclure dans la restauration de la base de données.  
  
Groupe de fichiers  **=**  { *nom_groupe_fichiers_logique* | **@***var_nom_groupe_fichiers_logique* }  
 Désigne un groupe de fichiers à inclure dans la restauration de la base de données.  
  
 **Remarque** FILEGROUP est autorisé en mode de récupération simple uniquement si le groupe de fichiers spécifié est en lecture seule et il s’agit d’une restauration partielle (autrement dit, si WITH PARTIAL est utilisé). Tout groupe de fichiers en lecture/écriture non restauré est indiqué dans un état défunt et ne peut être ensuite restauré dans la base de données résultante.  
  
READ_WRITE_FILEGROUPS  
 Sélectionne tous les groupes de fichiers en lecture/écriture. Cette option s'avère particulièrement utile lorsque vous disposez de groupes de fichiers en lecture seule à restaurer après des groupes de fichiers en lecture/écriture et avant les groupes de fichiers en lecture seule.  
  
PAGE = **'***fichier***:***page* [ **,**... *n* ]**'**  
 Spécifie une liste d'une ou plusieurs pages pour une restauration de pages (disponible uniquement pour les bases de données qui utilisent le mode de restauration complète ou le mode de récupération utilisant les journaux de transactions). Les valeurs sont les suivantes :  
  
PAGE  
 Indique une liste d'un ou plusieurs fichiers et d'une ou plusieurs pages.  
  
 *fichier*  
 ID du fichier contenant une page spécifique à restaurer.  
  
 *page*  
 ID de la page à restaurer dans le fichier.  
  
 *n*  
 Espace réservé indiquant que plusieurs pages peuvent être spécifiées.  
  
 Le nombre maximal des pages qui peuvent être restaurées dans un fichier unique au cours d'une séquence de restauration est 1 000. Cependant, si vous disposez d'un nombre de pages endommagées plus important dans un fichier, pensez à restaurer la totalité du fichier au lieu des pages en question.  
  
> [!NOTE]  
>  Les restaurations de pages ne sont jamais récupérées.  
  
 Pour plus d’informations sur la restauration de pages, consultez [restaurer des Pages &#40; SQL Server &#41; ](../../relational-databases/backup-restore/restore-pages-sql-server.md).  
  
 [ **,**...*n* ]  
 Espace réservé indiquant qu'il est possible de spécifier plusieurs fichiers, groupes de fichiers et pages dans une liste séparée par des virgules. Le nombre est illimité.  
  
À partir de { \<backup_device > [ **,**... *n* ]| \<database_snapshot >} En général, spécifie les unités de sauvegarde à partir duquel restaurer la sauvegarde. Sinon, dans une instruction RESTORE DATABASE, la clause FROM peut spécifier le nom d'un instantané de base de données vers lequel vous restaurez la base de données, auquel cas, aucune clause WITH n'est autorisée.  
  
 Si la clause FROM est omise, la restauration de la sauvegarde n'a pas lieu. À la place, la base de données est récupérée. Cela vous permet de récupérer une base de données restaurée avec l'option NORECOVERY, ou de basculer vers un serveur de secours. Si la clause FROM est omise, il convient de spécifier NORECOVERY, RECOVERY ou STANDBY dans la clause WITH.  
  
 \<unité_sauvegarde > [ **,**...  *n*  ] Spécifie les unités de sauvegarde logiques ou physiques à utiliser pour l’opération de restauration.  
  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), [RESTORE REWINDONLY](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 \<unité_sauvegarde > :: = Spécifie une unité de sauvegarde logique ou physique à utiliser pour l’opération de sauvegarde, comme suit :  
  
 { *logical_backup_device_name* | **@***logical_backup_device_name_var* }  
 Nom logique, qui doit respecter les règles des identificateurs, de l’unité de sauvegarde créée par **sp_addumpdevice** à partir de laquelle la base de données est restaurée. Fourni comme variable (**@***logical_backup_device_name_var*), le nom de l’unité de sauvegarde peut être spécifié comme constante de chaîne (**@***logical_backup_device_name_var* = *logical_backup_device_name*) ou comme une variable de type chaîne de caractères, à l’exception de la **ntext** ou **texte** des types de données.  
  
 {DISQUE | BANDE}  **=**  { **'***nom_unité_sauvegarde_physique***'** | **@***nom_unité_sauvegarde_physique_var* }  
 Permet la restauration de sauvegardes à partir de l'unité de disque ou de bande spécifiée. Les types d’appareils de disk et tape doivent être spécifiés avec le nom réel (par exemple, chemin d’accès et nom complet) de l’appareil : `DISK ='Z:\SQLServerBackups\AdventureWorks.bak'` ou `TAPE ='\\\\.\TAPE0'`. S’il est spécifié en tant que variable (**@***physical_backup_device_name_var*), le nom du périphérique peut être spécifié comme constante de chaîne (**@***physical_backup_device_name_var* = '*physcial_backup_device_name*') ou comme une variable de type chaîne de caractères, à l’exception de la **ntext** ou **texte** des types de données.  
  
 Si vous utilisez un serveur réseau pourvu d'un nom UNC (qui doit contenir le nom de l'ordinateur), spécifiez le type d'unité DISK. Pour plus d’informations sur la façon d’utiliser des noms UNC, consultez [unités de sauvegarde &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 Le compte sous lequel vous exécutez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit disposer d'un accès en lecture (READ) au serveur de réseau ou à l'ordinateur distant pour effectuer une opération RESTORE.  
  
 *n*  
 Est un espace réservé indiquant que jusqu'à 64 unités de sauvegarde peut-être être spécifié dans une liste séparée par des virgules.  
  
 Pour savoir si une séquence de restauration nécessite autant d'unités de sauvegarde que celles utilisées pour créer le support de sauvegarde auquel appartiennent les sauvegardes, vous devez tenir compte du fait que la restauration s'effectue hors connexion ou bien en ligne, conformément à ce qui suit :  
  
-   La restauration hors ligne permet de restaurer une sauvegarde en utilisant moins d'unités que le nombre nécessaire pour créer la sauvegarde.  
  
-   La restauration en ligne nécessite toutes les unités de sauvegarde. Toute tentative avec un nombre d'unités inférieur échoue.  
  
 Étudions, par exemple, un cas dans lequel une base de données a été sauvegardée sur quatre lecteurs de bande reliés au serveur. Une restauration en ligne nécessite que vous disposiez de quatre lecteurs de bande connectés au serveur ; une restauration hors connexion vous permet de restaurer la sauvegarde si l'ordinateur comprend moins de quatre lecteurs.  
  
> [!NOTE]  
>  Lors de la restauration d'une sauvegarde à partir d'un support de sauvegarde miroir, vous ne pouvez spécifier qu'un seul miroir pour chaque famille de supports. En cas d'erreurs, cependant, l'utilisation d'autres miroirs permet une résolution rapide de certains problèmes de restauration. Vous pouvez remplacer un volume de supports endommagé par le volume correspondant d'un autre miroir. Sachez que pour les restaurations hors connexion, vous pouvez effectuer la restauration à partir d'un nombre de supports inférieur au nombre de familles de supports, mais que chaque famille n'est traitée qu'une seule fois.  
  
\<database_snapshot > :: =  
**Prise en charge par :**[restauration de base de données  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
DATABASE_SNAPSHOT  **=**  *nom_instantané_base_de_données*  
 Rétablit la base de données à l’instantané de base de données spécifiée par *nom_instantané_base_de_données*. L'option DATABASE_SNAPSHOT est disponible uniquement pour une restauration de base de données complète. Lors d'une opération de rétablissement, l'instantané de la base de données remplace une sauvegarde de base de données complète.  
  
 Une opération de rétablissement nécessite que l'instantané de base de données spécifié soit l'unique sur la base de données. Au cours de l'opération de restauration, l'instantané de base de données et la base de données de destination sont tous deux indiqués comme `In restore`. Pour plus d’informations, consultez la section « Remarques » dans [restaurer la base de données](../../t-sql/statements/restore-statements-transact-sql.md).  
  
### <a name="with-options"></a>Options WITH  
 Spécifie les options à utiliser lors de l'opération de restauration. Pour obtenir un résumé permettant de savoir quelles instructions utilisent quelle option, consultez « Résumé de prise en charge des options WITH », plus loin dans ce chapitre.  
  
> [!NOTE]  
>  Options WITH sont organisées ici dans le même ordre que dans la section « Syntaxe » dans [Restaurer {base de données | JOURNAL}](../../t-sql/statements/restore-statements-transact-sql.md).  
  
 PARTIAL  
 **Prise en charge par :**[restauration de base de données  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Spécifie une opération de restauration partielle qui restaure le groupe de fichiers primaire et tout groupe de fichiers secondaire indiqué. L'option PARTIAL sélectionne implicitement le groupe de fichiers primaire, en spécifiant que FILEGROUP = 'PRIMARY' n'est pas nécessaire. Pour restaurer un groupe de fichiers secondaire, vous devez explicitement spécifier le groupe de fichiers à l'aide de l'option FILE ou de l'option FILEGROUP.  
  
 L'option PARTIAL n'est pas autorisée sur des instructions RESTORE LOG.  
  
 L'option PARTIAL démarre l'étape initiale d'une restauration fragmentaire, qui permet la restauration ultérieure des groupes de fichiers restants. Pour plus d’informations, consultez [Restaurations fragmentaires &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md).  
  
 [ **RÉCUPÉRATION** | NORECOVERY | MISE EN VEILLE]  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 **RÉCUPÉRATION**  
 Permet d'imposer, pendant la restauration, l'annulation des transactions non validées. Après la récupération, la base de données est prête à l'emploi. Si aucune des options NORECOVERY, RECOVERY ou STANDBY n'est spécifiée, RECOVERY est choisie par défaut.  
  
 Si d'autres opérations RESTORE (RESTORE LOG ou RESTORE DATABASE) sont planifiées, il faut spécifier NORECOVERY ou STANDBY.  
  
 Lors de la restauration de jeux de sauvegarde à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il peut s'avérer nécessaire d'opérer une mise à niveau des bases de données. Cette mise à niveau est réalisée automatiquement lorsque WITH RECOVERY est spécifiée. Pour plus d’informations, consultez [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
> [!NOTE]  
>  Si la clause FROM est omise, il convient de spécifier NORECOVERY, RECOVERY ou STANDBY dans la clause WITH.  
  
 NORECOVERY  
 Permet d'empêcher, pendant la restauration, l'annulation des transactions non validées. Si un autre journal de transactions a été appliqué ultérieurement, spécifiez l'option NORECOVERY ou STANDBY. Si aucune des options NORECOVERY, RECOVERY ou STANDBY n'est spécifiée, RECOVERY est choisie par défaut. Au cours d'une opération de restauration hors connexion à l'aide de l'option NORECOVERY, la base de données n'est pas utilisable.  
  
 Pour la restauration d'une sauvegarde de base de données et d'un ou de plusieurs journaux de transactions, ou lorsque plusieurs instructions RESTORE sont nécessaires (par exemple en cas de sauvegarde complète d'une base suivie d'une sauvegarde différentielle), RESTORE nécessite l'utilisation de l'option WITH NORECOVERY sur toutes les instructions RESTORE, sauf sur la dernière. Une des méthodes recommandées consiste à utiliser WITH NORECOVERY sur TOUTES les instructions dans une séquence de restauration à plusieurs étapes jusqu'à atteindre le point de récupération souhaité, puis d'utiliser une instruction RESTORE WITH RECOVERY séparée pour la récupération uniquement.  
  
 Employée lors de la restauration d'un fichier ou d'un groupe de fichiers, NORECOVERY oblige la base de données à rester dans l'état de restauration lorsque la restauration est terminée. Cette option est utile dans l'une des situations suivantes :  
  
-   un script de restauration est en cours d'exécution et le journal est toujours appliqué ;  
  
-   une séquence de restaurations de fichiers est exécutée et il n'est pas nécessaire que la base soit utilisable entre les deux opérations de restauration.  
  
 Dans certains cas, RESTORE WITH NORECOVERY restaure la restauration par progression définie à un niveau suffisamment avancé afin d'assurer la cohérence avec la base de données. Dans ces cas, la restauration ne s'effectue pas et les données demeurent hors connexion, comme prévu avec cette option. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] émet cependant un message d'information qui indique que la restauration par progression définie peut dorénavant être récupérée à l'aide de l'option RECOVERY.  
  
Mise en veille  **=**  *nom_fichier_annulation*  
 Indique un fichier journal des annulations qui permet d'annuler les effets de la récupération. L'option STANDBY est autorisée pour la restauration hors connexion (y compris la restauration partielle). L'option est désactivée pour la restauration en ligne. Toute tentative de spécification de l'option STANDBY pour une opération de restauration en ligne entraîne l'échec de l'opération de restauration. STANDBY n'est pas non plus autorisée lorsqu'une mise à niveau de base de données est nécessaire.  
  
 Le fichier d'annulation sert à conserver une préimage « copie à l'écriture » pour les pages modifiées au cours de la validation de l'annulation de RESTORE WITH STANDBY. Le fichier d'annulation permet la constitution d'une base de données accessible en lecture seule entre les restaurations des journaux de transactions ; elle est utilisable avec des serveurs en état de secours semi-automatique ou pour des récupérations spéciales, lorsqu'il s'avère utile d'inspecter la base de données entre les restaurations de journal. Après une opération RESTORE WITH STANDBY, le fichier d'annulation est automatiquement supprimé par l'opération RESTORE suivante. Si ce fichier d'annulation est supprimé manuellement avant l'opération RESTORE suivante, alors la totalité de la base de données doit être à nouveau restaurée. Pendant que la base de données se trouve dans un état STANDBY, vous devez traiter ce fichier d'annulation avec la même attention que pour n'importe quel autre fichier de base de données. Contrairement aux autres fichiers de base de données, ce fichier est uniquement maintenu ouvert par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au cours des opérations de restauration actives.  
  
 Le *nom_fichier_annulation* spécifie un fichier d’annulation dont l’emplacement est stocké dans le journal de la base de données. Si un fichier existant utilise le nom spécifié, le fichier est remplacé ; sinon, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] crée le fichier.  
  
 La taille requise pour un fichier d'annulation spécifique dépend du volume d'actions d'annulation issues des transactions non validées au cours de la restauration.  
  
> [!IMPORTANT]  
>  S'il n'y a plus de place sur le disque contenant le fichier d'annulation indiqué, la restauration s'arrête.  
  
 Pour une comparaison entre RECOVERY et NORECOVERY, consultez la section « Remarques » dans [restaurer](../../t-sql/statements/restore-statements-transact-sql.md).  
  
LOADHISTORY  
 **Prise en charge par :**[RESTORE VERIFYONLY  ](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
 Spécifie que l’opération de restauration charge les informations dans le **msdb** tables d’historique. L’option LOADHISTORY TRANSFÈRE charge plus d’informations, le jeu de sauvegardes en cours de vérification, environ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sauvegardes stockées sur le support défini sur la sauvegarde et restauration des tables d’historique de la **msdb** base de données. Pour plus d’informations sur les tables d’historique, consultez [Tables système &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/system-tables-transact-sql.md).  
  
#### <a name="generalwithoptions--n-"></a>\<general_WITH_options > [,.. .n]  
 Les options WITH générales sont toutes prises en charge dans les instructions RESTORE DATABASE et RESTORE LOG. Certaines de ces options sont également pris en charge par une ou plusieurs instructions auxiliaires, comme indiqué ci-après.  
  
##### <a name="restore-operation-options"></a>Options de l'opération de restauration  
 Ces options affectent le comportement de l'opération de restauration.  
  
DÉPLACER **'***nom_fichier_logique_dans_sauvegarde***'** à **'***nom_fichier_système_exploitation***'** [... *n* ]  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md) et [RESTORE VERIFYONLY  ](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
 Spécifie que les données ou le journal fichier dont le nom logique est spécifié par *nom_fichier_logique_dans_sauvegarde* doit être déplacé en le restaurant à l’emplacement spécifié par *nom_fichier_système_exploitation*. Le nom de fichier logique d'un fichier de données ou journal dans un jeu de sauvegarde correspond au nom logique qu'il portait dans la base de données au moment de la création du jeu de sauvegarde.  
  
*n*est un espace réservé indiquant que vous pouvez spécifier des instructions MOVE supplémentaires. Spécifiez une instruction MOVE pour chaque fichier logique du jeu de sauvegarde que vous voulez restaurer à un nouvel emplacement. Par défaut, le *nom_fichier_logique_dans_sauvegarde* fichier est restauré à son emplacement d’origine.  
  
> [!NOTE]  
>  Utilisez RESTORE FILELISTONLY pour obtenir une liste des fichiers logiques contenus dans le jeu de sauvegarde.  
  
 Si une instruction RESTORE est utilisée pour déplacer une base de données sur le même serveur ou la copier sur un serveur différent, l'option MOVE peut s'avérer nécessaire afin de déplacer les fichiers de la base et d'éviter toute collision avec des fichiers existants.  
  
 Utilisée avec RESTORE LOG, l'option MOVE ne peut servir qu'à déplacer les fichiers qui ont été ajoutés au cours de l'intervalle couvert par le journal en cours de restauration. Si, par exemple, la sauvegarde du journal contient une opération d'ajout de fichier pour le fichier `file23`, ce fichier peut être déplacé à 'laide de l'option MOVE sur RESTORE LOG.  
  
 Lorsqu’il est utilisé avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instantané de sauvegarde, l’option MOVE peut être utilisée uniquement pour déplacer des fichiers vers un Azure blob dans le même compte de stockage que l’objet blob d’origine. L’option MOVE ne peut pas être utilisée pour restaurer la sauvegarde d’instantanés dans un fichier local ou à un autre compte de stockage.  
  
 Si une instruction RESTORE VERIFYONLY est utilisée lorsque vous prévoyez de déplacer une base de données sur le même serveur ou de la copier sur un serveur différent, l'option MOVE peut s'avérer nécessaire afin de vérifier que l'espace disponible est nécessaire sur la cible et d'identifier les collisions éventuelles avec des fichiers existants.  
  
 Pour plus d’informations, consultez [Copier des bases de données avec la sauvegarde et la restauration](../../relational-databases/databases/copy-databases-with-backup-and-restore.md).  
  
CREDENTIAL  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2 et[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Utilisé uniquement lors de la restauration d’une sauvegarde à partir du service de stockage d’objets Blob Microsoft Azure.  
  
> [!NOTE]  
>  Avec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2 jusqu'à ce que [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], vous ne pouvez restaurer à partir d’une seule unité lors de la restauration à partir de l’URL. Afin de restaurer à partir de plusieurs appareils lors de la restauration à partir de l’URL, vous devez utiliser [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)) et vous devez utiliser des jetons de Signature d’accès partagé (SAS). Pour plus d’informations, consultez [activer la sauvegarde managée SQL Server vers Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) et [simplification de la création des informations d’identification SQL avec des jetons de Signature d’accès partagé (SAS) sur le stockage Azure avec Powershell](http://blogs.msdn.com/b/sqlcat/archive/2015/03/21/simplifying-creation-sql-credentials-with-shared-access-signature-sas-keys-on-azure-storage-containers-with-powershell.aspx).  
  
 REPLACE  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit créer la base de données spécifiée et ses fichiers même s'il en existe une autre de même nom. En pareil cas, la base existante est supprimée. Lorsque l'option REPLACE n'est pas précisée, une vérification a lieu. Celle-ci évite le remplacement accidentel d'une autre base de données. Cette vérification garantit que l'instruction RESTORE DATABASE ne restaure pas la base de données sur le serveur courant si les deux conditions suivantes existent :  
  
-   la base de données nommée dans l'instruction RESTORE existe déjà sur le serveur en cours, et  
  
-   le nom de la base est différent du nom enregistré dans le jeu de sauvegarde.  
  
 REPLACE permet également à RESTORE de remplacer un fichier existant dont il est impossible de vérifier qu'il appartient à la base de données en cours de restauration. Normalement, RESTORE refuse de remplacer les fichiers existants. WITH REPLACE peut aussi être utilisé de la même manière que l'option RESTORE LOG.  
  
 REPLACE supplante également la nécessité de sauvegarder la fin du journal avant la restauration de la base de données.  
  
 Pour plus d’informations l’impact de l’utilisation de l’option REPLACE, consultez [restauration &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-transact-sql.md).  
  
RESTART  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit redémarrer une restauration qui a été interrompue. RESTART relance la restauration au point de son interruption.  
  
RESTRICTED_USER  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md).  
  
 Restreint l’accès à la base de données nouvellement restaurée aux membres de la **db_owner**, **dbcreator**, ou **sysadmin** rôles.  RESTRICTED_USER remplace l'option DBO_ONLY. L'option DBO_ONLY a été supprimée dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 Utilisez avec l'option RECOVERY.  
  
##### <a name="backup-set-options"></a>Options du jeu de sauvegarde  
 Ces options se rapportent au jeu de sauvegarde qui contient la sauvegarde à restaurer.  
  
FICHIER  **=** { *numéro_fichier_jeu_sauvegarde* | **@***numéro_fichier_jeu_sauvegarde* }  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 Identifie le jeu de sauvegarde à restaurer. Ainsi, une valeur *numéro_fichier_jeu_sauvegarde* égale à **1** indique le premier jeu de sauvegarde sur le support de sauvegarde, et une valeur *numéro_fichier_jeu_sauvegarde* égale à **2** indique le second jeu. Vous pouvez obtenir le *numéro_fichier_jeu_sauvegarde* d’un jeu de sauvegarde en utilisant l’instruction [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) .  
  
 Lorsque ne pas spécifié, la valeur par défaut est **1**, sauf pour RESTORE HEADERONLY auquel cas tous les jeux de sauvegarde dans le jeu de supports sont traités. Pour plus d'informations, consultez « Spécification d'un jeu de sauvegarde » plus loin dans cette rubrique.  
  
> [!IMPORTANT]  
>  Cette option de fichier n’est pas liée à l’option de fichier pour la spécification d’un fichier de base de données, fichier  **=**  { *nom_fichier_logique_dans_sauvegarde* | **@***logical_file_name_in_backup_var* }.  
  
 Mot de passe  **=**  { *mot de passe* | **@***password_variable* }  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 Fournit le mot de passe du jeu de sauvegarde. Un mot de passe de jeu de sauvegarde est une chaîne de caractères.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Si un mot de passe a été spécifié lors de la création du jeu de sauvegarde, il est requis lors de chaque opération de restauration à partir du jeu de sauvegarde. La spécification d'un mot de passe incorrect ou d'un mot de passe pour un jeu de sauvegarde qui n'en possède pas constitue une erreur.  
  
> [!IMPORTANT]  
>  Ce mot de passe fournit uniquement une protection faible pour le support de sauvegarde. Pour plus d'informations, consultez la section « Autorisations » pour la rubrique adéquate.  
  
##### <a name="media-set-options"></a>Options du support de sauvegarde  
 Ces options s'appliquent à l'ensemble du support de sauvegarde.  
  
 MEDIANAME  **=**  { *nom_support* | **@***variable_nom_support*}  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 Indique le nom du support. S'il est fourni, le nom du support doit correspondre au nom des volumes de sauvegarde ; sinon, l'opération de restauration prend fin. En l'absence de nom de support dans l'instruction RESTORE, aucun contrôle n'a lieu pour vérifier la correspondance des noms de support sur les volumes de sauvegarde.  
  
> [!IMPORTANT]  
>  L'emploi cohérent de noms de support dans les opérations de sauvegarde et de restauration offre une garantie supplémentaire de sécurité lors du choix des supports de restauration.  
  
 MEDIAPASSWORD  **=**  { *mediapassword* | **@***mediapassword_variable* }  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 Fournit le mot de passe du support de sauvegarde. Un mot de passe de jeu de supports est une chaîne de caractères.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Si un mot de passe a été fourni lors du formatage du support de sauvegarde, il est requis pour accéder à tout jeu de sauvegarde sur le jeu de supports. La spécification d'un mot de passe incorrect ou d'un mot de passe pour un support de sauvegarde qui n'en possède pas constitue une erreur.  
  
> [!IMPORTANT]  
>  Ce mot de passe fournit uniquement une protection faible pour le support de sauvegarde. Pour plus d’informations, consultez la section « Autorisations » pour la déclaration.  
  
 BLOCKSIZE  **=**  { *blocksize* | **@***variable_taille_bloc* }  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Indique, en octets, la taille physique du bloc. Les tailles prises en charge sont 512, 1024, 2048, 4096, 8192, 16384, 32768 et 65536 (64 Ko) octets. La valeur par défaut est 65536 pour les périphériques à bandes, 512 sinon. En règle générale, cette option est superflue car RESTORE sélectionne automatiquement une taille de bloc appropriée pour le périphérique. Si vous spécifiez explicitement une taille de bloc, la sélection automatique est annulée et remplacée.  
  
 Si vous restaurez une sauvegarde à partir d'un CD-ROM, spécifiez BLOCKSIZE=2048.  
  
> [!NOTE]  
>  En règle générale, cette option n'affecte les performances que si les données sont lues sur des périphériques à bandes.  
  
##### <a name="data-transfer-options"></a>Options de transfert de données  
 Ces options vous permettent d'optimiser le transfert de données à partir de l'unité de sauvegarde.  
  
 BUFFERCOUNT  **=**  { *buffercount* | **@***buffercount_variable* }  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Spécifie le nombre total de tampons d'E/S à utiliser pour l'opération de restauration. Vous pouvez spécifier n'importe quel entier positif ; toutefois, un nombre élevé de tampons peut provoquer des erreurs liées à une insuffisance de mémoire. En effet, l'espace d'adressage virtuel peut s'avérer inapproprié dans la tâche Sqlservr.exe.  
  
 L’espace total utilisé par les mémoires tampons est déterminé par : *buffercount***\****maxtransfersize*.  
  
 MAXTRANSFERSIZE  **=**  { *maxtransfersize* | **@***maxtransfersize_variable* }  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 Spécifie, en octets, la plus grande unité de transfert à utiliser entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le support de sauvegarde. Les valeurs possibles sont les multiples de 65536 octets (64 Ko), dans la limite de 4194304 octets (4 Mo).  
> [!NOTE]  
>  Lorsque la base de données a configuré FILESTREAM ou inclut ou groupes de fichiers OLTP en mémoire, `MAXTRANSFERSIZE` au moment de la restauration doit être supérieure ou égale à celle utilisée lorsque la sauvegarde a été créée.  
  
##### <a name="error-management-options"></a>Options de gestion des erreurs  
 Ces options permettent de déterminer si les sommes de contrôle de sauvegarde sont activées pour l’opération de restauration et indique si l’opération s’arrête en cas d’erreur.    
  
 { CHECKSUM | NO_CHECKSUM }  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 Le comportement par défaut consiste à vérifier des sommes de contrôle si elles sont présentes et à poursuivre sans vérification si elles ne le sont pas.  
  
 CHECKSUM  
 Spécifie que des sommes de contrôle de sauvegarde doivent être vérifiées et, si la sauvegarde manque de sommes de contrôle de sauvegarde, entraîne l'échec de l'opération de restauration avec un message indiquant que des sommes de contrôle ne sont pas présentes.  
  
> [!NOTE]  
>  Les sommes de contrôle de page sont pertinentes pour les opérations de sauvegarde uniquement si les sommes de contrôle de sauvegarde sont utilisées.  
  
 Par défaut, lors de la détection d'une somme de contrôle incorrecte, RESTORE signale une erreur de somme de contrôle et s'arrête. Cependant, si vous spécifiez CONTINUE_AFTER_ERROR, RESTORE continue après le renvoi d'une erreur de somme de contrôle et du numéro de la page contenant la somme de contrôle incorrecte, si la corruption le permet.  
  
 Pour plus d’informations sur l’utilisation des sommes de contrôle de sauvegarde, consultez [Possible Media erreurs au cours de sauvegarde et de restauration &#40; SQL Server &#41; ](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md).  
  
 NO_CHECKSUM  
 Désactive explicitement la validation de sommes de contrôle par l'opération de restauration.  
  
 { **STOP_ON_ERROR** | CONTINUE_AFTER_ERROR}  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 STOP_ON_ERROR  
 Spécifie que l'opération de restauration s'arrête à la première erreur rencontrée. Il s'agit du comportement par défaut pour RESTORE, sauf pour VERIFYONLY qui possède CONTINUE_AFTER_ERROR par défaut.  
  
 CONTINUE_AFTER_ERROR  
 Spécifie que l'opération de restauration doit continuer après la détection d'une erreur.  
  
 Si une sauvegarde contient des pages endommagées, il est préférable de répéter l'opération de restauration en utilisant une autre sauvegarde qui ne contient pas ces erreurs (par exemple, une sauvegarde effectuée avant que les pages aient été endommagées). Toutefois, en dernier ressort, vous pouvez restaurer une sauvegarde endommagée à l'aide de l'option CONTINUE_AFTER_ERROR de l'instruction RESTORE et essayer de sauver les données.  
  
##### <a name="filestream-options"></a>Options FILESTREAM  
 FILESTREAM (DIRECTORY_NAME =*directory_name* )  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md) et [RESTORE VERIFYONLY  ](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Nom de répertoire compatible avec Windows. Ce nom doit être unique parmi tous les noms de répertoire FILESTREAM au niveau de la base de données dans cette instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La comparaison d'unicité s'effectue sans respect de la casse, quels que soient les paramètres de classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##### <a name="monitoring-options"></a>Options de surveillance  
 Ces options vous permettent de surveiller le transfert des données à partir de l'unité de sauvegarde.  
  
 STATISTIQUES [  **=**  *pourcentage* ]  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md) et [RESTORE VERIFYONLY  ](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
 Affiche un message à chaque fois qu'un autre pourcentage se termine et sert à évaluer l'état d'avancement de l'opération. Si *pourcentage* est omis, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche un message à chaque 10 pour cent (approximativement).  
  
 L'option STATS signale le pourcentage terminé comme seuil de rapport de l'intervalle suivant. Cela se situe approximativement au pourcentage spécifié ; par exemple, avec STATS=10, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] crée un rapport à cet intervalle environ ; ainsi, au lieu d'afficher précisément 40 %, l'option peut afficher 43 %. Pour les jeux de sauvegarde volumineux, cela n'est pas un problème car le pourcentage d'achèvement progresse très lentement entre les appels d'E/S terminés.  
  
##### <a name="tape-options"></a>Options des périphériques à bandes  
 Ces options sont utilisées uniquement pour les périphériques À BANDES. S'il ne s'agit pas d'un périphérique à bandes, ces options sont ignorées.  
  
 { **REWIND** | NOREWIND }  
 Ces options sont utilisées uniquement pour les périphériques À BANDES. Si vous n'utilisez pas un périphérique à bandes, ces options sont ignorées.  
  
 REWIND  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] libère et rembobine la bande. REWIND est le paramètre par défaut.  
  
 NOREWIND  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md) et [RESTORE VERIFYONLY  ](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
 La spécification de NOREWIND dans n'importe quel autre argument de restauration génère une erreur.  
  
 Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintient la bande ouverte après l'opération de sauvegarde. Vous pouvez utiliser cette option pour améliorer les performances lorsque vous effectuez plusieurs opérations de sauvegarde sur bande.  
  
 NOREWIND implique NOUNLOAD, et ces options sont incompatibles dans une instruction RESTORE unique.  
  
> [!NOTE]  
>  Si vous utilisez NOREWIND, l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve la propriété du lecteur de bande jusqu'à ce qu’une instruction BACKUP ou RESTORE en cours d’exécution dans le même processus utilise le REWIND ou UNLOAD option ou de l’instance de serveur est arrêtée. Le fait de maintenir la bande ouverte empêche les autres processus d'y accéder. Pour plus d’informations sur la façon de pour afficher une liste des bandes ouvrir et fermer une bande ouverte, consultez [unités de sauvegarde &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 { **UNLOAD** | NOUNLOAD}  
 **Prise en charge par :**[restaurer](../../t-sql/statements/restore-statements-transact-sql.md), [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md), [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md), [RESTORE LABELONLY](../../t-sql/statements/restore-statements-labelonly-transact-sql.md), [RESTORE REWINDONLY](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md), et [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
 Ces options sont utilisées uniquement pour les périphériques À BANDES. Si vous n'utilisez pas un périphérique à bandes, ces options sont ignorées.  
  
> [!NOTE]  
>  UNLOAD/NOUNLOAD est un paramètre de session qui reste en vigueur jusqu'à la fin de la session ou tant qu'il n'est pas réinitialisé par le choix de l'option opposée à celle en cours d'utilisation.  
  
 UNLOAD  
 Indique que la bande est automatiquement rembobinée et démontée lorsque la sauvegarde est terminée. UNLOAD est l'option par défaut au démarrage d'une session.  
  
 NOUNLOAD  
 Spécifie qu’une fois l’opération de restauration de la bande reste chargée sur le lecteur de bande.  
  
#### <a name="replicationwithoption"></a>< replication_WITH_option >  
 Cette option est utile seulement si la base de données a été répliquée lors de la création de la sauvegarde.  
  
 KEEP_REPLICATION  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
Utiliser KEEP_REPLICATION lorsque vous configurez la réplication avec envoi de journaux. Cette option évite la suppression des paramètres de réplication lorsqu'une sauvegarde de base de données ou de journal est restaurée sur un serveur en état de secours semi-automatique et que la base de données est récupérée. Il est impossible de spécifier cette option lors de la restauration d'une sauvegarde avec l'option NORECOVERY. Pour garantir un fonctionnement correct de la réplication après la restauration :  
  
-   Le **msdb** et **master** bases de données au niveau du serveur de secours semi-automatique doivent être synchronisées avec le **msdb** et **master** bases de données sur le serveur principal.  
  
-   Le serveur en état de secours semi-automatique doit être renommé pour utiliser le même nom que le serveur primaire.  
  
#### <a name="changedatacapturewithoption"></a>< change_data_capture_WITH_option >  
 Cette option est utile seulement si la base de données a été activée pour la capture de données modifiées, lors de la création de la sauvegarde.  
  
 KEEP_CDC  
 **Prise en charge par :**[restaurer  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 KEEP_CDC doit être utilisé pour empêcher de modifier les paramètres de capture de données d’être supprimé lorsqu’une sauvegarde de base de données ou de la sauvegarde du journal est restaurée sur un autre serveur et la base de données est récupérée. Il est impossible de spécifier cette option lors de la restauration d'une sauvegarde avec l'option NORECOVERY.  
  
 Restauration de la base de données avec KEEP_CDC ne crée pas les travaux de capture de données modifiées. Pour extraire les modifications du journal après avoir restauré la base de données, recréez le travail de capture et le travail de nettoyage pour la base de données restaurée. Pour plus d’informations, consultez [sys.sp_cdc_add_job &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).  
  
 Pour plus d’informations sur l’utilisation de la capture de données modifiées avec la mise en miroir de base de données, consultez [Capture de données modifiées et autres fonctionnalités SQL Server](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md).  
  
#### <a name="servicebrokerwithoptions"></a>\<service_broker_WITH_options >  
 Active ou désactive la remise de messages [!INCLUDE[ssSB](../../includes/sssb-md.md)] ou définit un nouvel identificateur [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Cette option est utile seulement si [!INCLUDE[ssSB](../../includes/sssb-md.md)] a été activé pour la base de données lors de la création de la sauvegarde.  
  
 {ENABLE_BROKER | ERROR_BROKER_CONVERSATIONS | NEW_BROKER}  
 **Prise en charge par :**[restauration de base de données  ](../../t-sql/statements/restore-statements-transact-sql.md)  
  
 ENABLE_BROKER  
 Spécifie que [!INCLUDE[ssSB](../../includes/sssb-md.md)] remise des messages est activée à la fin de la restauration afin que les messages peuvent être envoyés immédiatement. Par défaut, la remise de messages [!INCLUDE[ssSB](../../includes/sssb-md.md)] est désactivée pendant une restauration. La base de données conserve l'identificateur Service Broker existant.  
  
 ERROR_BROKER_CONVERSATIONS  
 Termine toutes les conversations avec une erreur indiquant que la base de données est attachée ou restaurée. De cette façon, vos applications peuvent effectuer un nettoyage standard des conversations existantes. La remise des messages Service Broker est désactivée jusqu'à la fin de l'opération, puis est réactivée. La base de données conserve l'identificateur Service Broker existant.  
  
 NEW_BROKER  
 Spécifie qu'un nouvel identificateur Service Broker doit être assigné à la base de données. Dans la mesure où la base de données est considérée comme un nouveau Service Broker, toutes les conversations existantes dans la base de données sont immédiatement supprimées sans générer de message de fin de dialogue. Tout itinéraire faisant référence à l'ancien identificateur Service Broker doit être recréé avec le nouvel identificateur.  
  
#### <a name="pointintimewithoptions"></a>\<point_in_time_WITH_options >  
 **Prise en charge par :**[Restaurer {base de données | JOURNAL}](../../t-sql/statements/restore-statements-transact-sql.md) et uniquement pour les modèles de récupération complet ou journalisé en bloc.  
  
 Vous pouvez restaurer une base de donnés à un point dans le temps ou une transaction spécifique en spécifiant le point de récupération cible dans une clause STOPAT, STOPATMARK ou STOPBEFOREMARK. Un point dans le temps ou une transaction spécifié(e) est toujours restauré(e) à partir d'une sauvegarde du journal. Dans chaque instruction RESTORE LOG de la séquence de restauration, vous devez spécifier votre point dans le temps ou transaction cible dans une clause STOPAT, STOPATMARK ou STOPBEFOREMARK identique.  
  
 En guise de condition préalable à une restauration limitée dans le temps, vous devez tout d'abord restaurer une sauvegarde de base de données complète dont le point de terminaison est antérieur à votre point de récupération cible. Pour vous aider à identifier la sauvegarde de base de données à restaurer, vous pouvez éventuellement spécifier votre clause WITH STOPAT, STOPATMARK ou STOPBEFOREMARK dans une instruction RESTORE DATABASE pour générer une erreur si une sauvegarde des données est trop récente pour le point dans le temps cible spécifié. Cependant, la sauvegarde de données complète est toujours restaurée, même si elle contient le point dans le temps cible.  
  
> [!NOTE]  
>  Le RESTORE_DATABASE et RESTORE_LOG point-à-temps WITH options sont similaires, mais seul RESTORE LOG prend en charge la *nom_marque* argument.  
  
 { STOPAT | STOPATMARK | STOPBEFOREMARK }   
 
 STOPAT  **=**  { **'***datetime***'** | **@***datetime_var* }  
 Spécifie que la base de données restaurée à l’état, il se trouvait à la date et l’heure spécifiée par le *datetime* ou  **@**  *datetime_var* paramètre. Pour plus d’informations sur la spécification d’une date et heure, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 Si une variable est utilisée pour STOPAT, elle doit être **varchar**, **char**, **smalldatetime**, ou **datetime** type de données. Seuls les enregistrements de journal écrits avant la date et l'heure spécifiées seront appliqués à la base de données.  
  
> [!NOTE]  
>  Si l'heure STOPAT spécifiée est postérieure à la dernière sauvegarde LOG, la base de données reste dans l'état de non restauration, comme si RESTORE LOG avait été exécuté avec NORECOVERY.  
  
 Pour plus d’informations, consultez [Restaurer une base de données SQL Server jusqu’à une limite dans le temps &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).  
  
 STOPATMARK  **=**  { **'***nom_marque***'** | **'**lsn :*numéro_lsn***'** } [AFTER **'***datetime***'** ]  
 Indique une récupération à un point de récupération donné. La transaction spécifiée est incluse dans la récupération, mais elle n'est validée que si elle a été validée à l'origine lors de la véritable génération de la transaction.  
  
 RESTORE DATABASE et RESTORE LOG prennent en charge la *numéro_lsn* paramètre. Ce paramètre spécifie un numéro séquentiel dans le journal.  
  
 Le *nom_marque* paramètre est pris en charge uniquement par l’instruction RESTORE LOG. Ce paramètre identifie une marque de transaction dans la sauvegarde du fichier journal.  
  
 Dans une instruction RESTORE LOG, si, après avoir *datetime* est omis, la récupération s’arrête à la première marque portant le nom spécifié. Si, après avoir *datetime* est spécifié, la récupération s’arrête à la première marque portant le nom spécifié à exactement ou après *datetime*.  
  
> [!NOTE]  
>  Si l'heure, la marque ou le NSE spécifié est postérieur à la dernière sauvegarde LOG, la base de données reste dans l'état de non restauration, comme si RESTORE LOG avait été exécuté avec NORECOVERY.  
  
 Pour plus d’informations, consultez [utiliser les Transactions marquées pour récupérer des bases de données associées uniformément &#40; Mode de récupération complète &#41; ](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md) et [récupérer un numéro de séquence du journal &#40; SQL Server &#41; ](../../relational-databases/backup-restore/recover-to-a-log-sequence-number-sql-server.md).  
  
 STOPBEFOREMARK  **=**  { **'***nom_marque***'** | **'**lsn :*numéro_lsn***'** } [AFTER **'***datetime***'** ]  
 Indique une récupération jusqu'à un point de récupération donné. La transaction spécifiée n'est pas incluse dans la récupération et est restaurée lorsque WITH RECOVERY est utilisé.  
  
 RESTORE DATABASE et RESTORE LOG prennent en charge la *numéro_lsn* paramètre. Ce paramètre spécifie un numéro séquentiel dans le journal.  
  
 Le *nom_marque* paramètre est pris en charge uniquement par l’instruction RESTORE LOG. Ce paramètre identifie une marque de transaction dans la sauvegarde du fichier journal.  
  
 Dans une instruction RESTORE LOG, si, après avoir *datetime* est omis, la récupération s’arrête juste avant la première marque portant le nom spécifié. Si, après avoir *datetime* est spécifié, la récupération s’arrête juste avant la première marque portant le nom spécifié à exactement ou après *datetime*.  
  
> [!IMPORTANT]  
>  Si une séquence de restauration partielle exclut tout groupe de fichiers FILESTREAM, la restauration limitée dans le temps n'est pas prise en charge. Vous pouvez forcer la séquence de restauration à continuer. Cependant, les groupes de fichiers FILESTREAM omis de l'instruction RESTORE ne pourront jamais être restaurés. Pour forcer une restauration limitée dans le temps, spécifiez l'option CONTINUE_AFTER_ERROR avec l'option STOPAT, STOPATMARK ou STOPBEFOREMARK. Si vous spécifiez l'option CONTINUE_AFTER_ERROR, la séquence de restauration partielle réussit et le groupe de fichiers FILESTREAM devient irrécupérable.  
  
## <a name="result-sets"></a>Jeux de résultats  
 Pour les jeux de résultats, consultez les rubriques suivantes :  
  
-   [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
-   [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)  
  
## <a name="remarks"></a>Notes  
 Pour des remarques supplémentaires, consultez les rubriques suivantes :  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
-   [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)  
  
-   [RESTORE REWINDONLY &#40; Transact-SQL &#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)  
  
-   [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
## <a name="specifying-a-backup-set"></a>Spécification d'un jeu de sauvegarde  
 A *jeu de sauvegarde* contient la sauvegarde à partir d’une opération de sauvegarde unique réussie. Les instructions RESTORE, RESTORE FILELISTONLY, RESTORE HEADERONLY et RESTORE VERIFYONLY fonctionnent sur un jeu de sauvegarde unique dans le jeu de médias sur la ou les unités de sauvegarde spécifiées. Vous devez spécifier la sauvegarde requise à partir du jeu de médias. Vous pouvez obtenir le *numéro_fichier_jeu_sauvegarde* d’un jeu de sauvegarde en utilisant l’instruction [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) .  
  
 L'option permettant de spécifier le jeu de sauvegarde à restaurer est la suivante :  
  
 FICHIER  **=** { *numéro_fichier_jeu_sauvegarde* | **@***numéro_fichier_jeu_sauvegarde* }  
  
 Où *numéro_fichier_jeu_sauvegarde* indique la position de la sauvegarde dans le jeu de supports. A *numéro_fichier_jeu_sauvegarde* 1 (fichier = 1) indique la premier jeu de sauvegarde sur le support de sauvegarde et un *numéro_fichier_jeu_sauvegarde* 2 (fichier = 2) indique le deuxième jeu de sauvegarde et ainsi de suite.  
  
 Le comportement de cette option varie en fonction de l’instruction, comme décrit dans le tableau suivant :  
  
|.|Comportement de l'option FILE du jeu de sauvegarde|  
|---------------|-----------------------------------------|  
|RESTORE|Le numéro par défaut du fichier de jeu de sauvegarde est 1. Seule une option FILE de jeu de sauvegarde est autorisée dans une instruction RESTORE. Il est important de spécifier les jeux de sauvegarde dans l'ordre.|  
|RESTORE FILELISTONLY|Le numéro par défaut du fichier de jeu de sauvegarde est 1.|  
|RESTORE HEADERONLY|Par défaut, tous les jeux de sauvegarde du support sont traités. Le jeu de résultats RESTORE HEADERONLY renvoie des informations sur chaque jeu de sauvegarde, y compris son **Position** dans le média défini. Pour renvoyer des informations sur un jeu de sauvegarde donné, utilisez son numéro de position en tant que le *numéro_fichier_jeu_sauvegarde* valeur dans l’option de fichier.<br /><br /> Remarque : Pour les bandes, RESTORE HEADER ne traite des jeux de sauvegarde sur la bande chargée.|  
|RESTORE VERIFYONLY|La valeur par défaut *numéro_fichier_jeu_sauvegarde* est 1.|  
  
> [!NOTE]  
>  L’option de fichier pour la spécification d’un jeu de sauvegarde n’est pas liée à l’option de fichier pour la spécification d’un fichier de base de données, fichier  **=**  { *nom_fichier_logique_dans_sauvegarde* | **@***logical_file_name_in_backup_var* }.  
  
## <a name="summary-of-support-for-with-options"></a>Résumé de prise en charge des options WITH  
 Les options WITH suivantes sont prises en charge uniquement par l’instruction RESTORE : BLOCKSIZE, BUFFERCOUNT, MAXTRANSFERSIZE, PARTIAL, KEEP_REPLICATION, {RECOVERY | NORECOVERY | STANDBY}, REPLACE, RESTART, RESTRICTED_USER et {STOPAT | STOPATMARK | STOPBEFOREMARK}  
  
> [!NOTE]  
>  L'option PARTIAL est uniquement prise en charge par RESTORE DATABASE.  
  
 Le tableau suivant répertorie les options WITH utilisées par une ou plusieurs instructions et indique quelles instructions prennent en charge quelle option. Une coche (√) indique qu'une option est prise en charge ; un tiret (—) signale qu'une option n'est pas prise en charge.  
  
|Option WITH|RESTORE|RESTORE FILELISTONLY|RESTORE HEADERONLY|RESTORE LABELONLY|RESTORE REWINDONLY|RESTORE VERIFYONLY|  
|-----------------|-------------|--------------------------|------------------------|-----------------------|------------------------|------------------------|  
|{ CHECKSUM<br /><br /> &#124; NO_CHECKSUM}|√|√|√|√|—|√|  
|{ CONTINUE_AFTER_ERROR<br /><br /> &#124; STOP_ON_ERROR}|√|√|√|√|—|√|  
|FICHIER<sup>1</sup>|√|√|√|—|—|√|  
|LOADHISTORY|—|—|—|—|—|√|  
|MEDIANAME|√|√|√|√|—|√|  
|MEDIAPASSWORD|√|√|√|√|—|√|  
|MOVE|√|—|—|—|—|√|  
|PASSWORD|√|√|√|—|—|√|  
|{REWIND &#124; NOREWIND}|√|REWIND uniquement|REWIND uniquement|REWIND uniquement|—|√|  
|STATS|√|—|—|—|—|√|  
|{UNLOAD &#124; NOUNLOAD}|√|√|√|√|√|√|  
  
 <sup>1</sup> fichier  **=**  *numéro_fichier_jeu_sauvegarde*, qui est différent de {fichier | GROUPE DE FICHIERS}.  
  
## <a name="permissions"></a>Permissions  
 Pour les autorisations, consultez les rubriques suivantes :  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
-   [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
-   [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)  
  
-   [RESTORE REWINDONLY &#40; Transact-SQL &#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)  
  
-   [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
## <a name="examples"></a>Exemples  
 Pour les exemples, consultez les rubriques suivantes :  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
-   [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
-   [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [Sauvegarde et restauration des bases de données SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
  
  

