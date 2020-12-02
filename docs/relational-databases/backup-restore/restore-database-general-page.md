---
title: Restaurer la base de données (page Général) | Microsoft Docs
description: Lorsque vous restaurez une base de données dans SQL Server, utilisez la page Général pour spécifier des informations sur les bases de données cible et source.
ms.custom: ''
ms.date: 09/28/2020
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restoredb.general.f1
ms.assetid: 160cf58c-b06a-475f-9a69-2b051e5767ab
author: cawrites
ms.author: chadam
ms.openlocfilehash: cda87fffca686f8e86c7b617e502952341bd459f
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125550"
---
# <a name="restore-database-general-page"></a>Restaurer la base de données (page Général)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Utilisez la page **Général** pour spécifier des informations sur les bases de données cible et source dans le cadre d’une opération de restauration de base de données.  
    
-   [Restaurer une sauvegarde de base de données à l’aide de SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  Quand vous spécifiez une tâche de restauration à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez générer le script [!INCLUDE[tsql](../../includes/tsql-md.md)] [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) correspondant en cliquant sur **Script**, puis en sélectionnant une destination pour le script.  
  
## <a name="permissions"></a>Autorisations  
Pour restaurer (RESTORE) une base de données qui n’existe pas, l’utilisateur doit disposer des autorisations CREATE DATABASE. Les autorisations de restauration (RESTORE) reviennent par défaut aux membres des rôles serveur fixes **sysadmin** et **dbcreator**, et au propriétaire (**dbo**) pour les bases de données existantes.  

Les informations d’appartenance pour les rôles qui ont des autorisations de restauration (RESTORE) sont toujours disponibles sur l’instance.

Dans une base de données accessible et non endommagée, une appartenance à un rôle de base de données fixe peut être vérifiée. Les membres du rôle de base de données fixe **db_owner** ne disposent pas des autorisations de restauration (RESTORE).  

Une appartenance à un rôle de base de données fixe peut être vérifiée seulement si la base de données est accessible et n’est pas endommagée. Ce n’est pas toujours le cas lors de l’exécution de RESTORE ; les membres du rôle de base de données fixe **db_owner** ne disposent pas des autorisations de restauration (RESTORE).  

Les autorisations RESTORE sont attribuées aux rôles dont les informations d'appartenance sont toujours immédiatement accessibles à partir du serveur. Une appartenance à un rôle de base de données fixe peut être vérifiée seulement si la base de données est accessible et n’est pas endommagée. Régulièrement, lors de l’exécution de RESTORE, les membres du rôle de base de données fixe **db_owner** ne disposent pas des autorisations de restauration (RESTORE).  

La restauration depuis une sauvegarde chiffrée requiert des autorisations **VIEW DEFINITION** pour accéder au certificat ou à la clé asymétrique qui a servi au chiffrement lors de la sauvegarde.  
  
## <a name="options"></a>Options  
  
### <a name="source"></a>Source  

Ces options identifient l’emplacement des jeux de sauvegarde pour la base de données ainsi que les jeux de sauvegarde que vous voulez restaurer.  
  
|Terme|Définition|  
|----------|----------------|  
|**Sauvegarde de la base de données**|Sélectionnez la base de données à restaurer dans la liste déroulante. La liste contient uniquement les bases de données qui ont été sauvegardées d’après l’historique de sauvegarde de **msdb**.|  
|**Appareil**|Sélectionnez les unités de sauvegarde logiques ou physiques (bandes, URL ou fichiers) qui contiennent la ou les sauvegardes à restaurer. L’unité est obligatoire si la sauvegarde de la base de données a été effectuée sur une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Pour sélectionner une ou plusieurs unités de sauvegarde logiques ou physiques, sélectionnez le bouton Parcourir afin d’ouvrir la boîte de dialogue **Sélectionner les unités de sauvegarde**. Dans cette boîte de dialogue, vous pouvez sélectionner jusqu'à 64 unités appartenant au même support de sauvegarde. Les lecteurs de bande doivent être connectés physiquement à l'ordinateur qui exécute l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un fichier de sauvegarde peut se trouver sur une unité de disque locale ou distante. Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md). Vous pouvez également sélectionner **URL** comme type de périphérique pour sauvegarder les fichiers stockés dans le stockage Azure.<br /><br /> Quand vous fermez la boîte de dialogue **Sélectionner les unités de sauvegarde** , l’unité sélectionnée s’affiche sous forme de valeurs accessibles en lecture seule dans la liste **Unité** .|  
|**Sauvegarde de la base de données**|Sélectionnez dans la liste déroulante le nom de la base de données depuis laquelle les sauvegardes doivent être restaurées.<br /><br /> Remarque : Cette liste n’est disponible que quand **Unité** est sélectionné. Seules les bases de données qui ont des copies de sauvegarde sur les unités sélectionnées sont disponibles.|  
  
### <a name="destination"></a>Destination  
 Les options du volet **Restaurer sur** identifient la base de données et le point de restauration.  
  
|Terme|Définition|  
|----------|----------------|  
|**Sauvegarde de la base de données**|Entrez la base de données à restaurer dans la liste. Vous pouvez entrer une nouvelle base de données ou choisir une base de données existante dans la liste déroulante. La liste contient toutes les bases de données sur le serveur, à l'exception des bases de données système **master** et **tempdb**.<br /><br /> Remarque : Pour restaurer une sauvegarde protégée par mot de passe, vous devez utiliser l’instruction [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) .|  
|**Restaurer sur**|Par défaut, la zone **Restaurer sur** a la valeur « Dernière sauvegarde effectuée ». Vous pouvez également sélectionner **Chronologie** pour ouvrir la boîte de dialogue **Chronologie de sauvegarde**, qui affiche l’historique des sauvegardes de la base de données sous forme de chronologie. Sélectionnez **Chronologie** pour choisir une **date/heure** spécifique jusqu’où restaurer la base de données. La base de données est ensuite restaurée dans l’état où elle se trouvait à ce moment spécifié. Consultez [Backup Timeline](../../relational-databases/backup-restore/backup-timeline.md).|  
  
### <a name="restore-plan"></a>Plan de restauration  
  
|Terme|Définition|Valeurs|  
|----------|----------------|------------|  
|**Jeux de sauvegarde à restaurer**|Affiche les jeux de sauvegarde disponibles pour l'emplacement indiqué. Une opération de sauvegarde crée un jeu de sauvegarde qui est distribué sur toutes les unités du jeu de supports. Par défaut, un plan de récupération est proposé pour accomplir l'opération de restauration basée sur la sélection des jeux de sauvegarde requis. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise l’historique des sauvegardes dans **msdb**. L’historique est utilisé pour identifier les sauvegardes nécessaires à la restauration d’une base de données et pour créer un plan de restauration. Par exemple, pour une restauration de base de données, le plan de restauration sélectionne la sauvegarde de base de données complète la plus récente, suivie de la sauvegarde de base de données différentielle la plus récente (le cas échéant). Avec le mode de récupération complète, le plan de restauration sélectionne ensuite toutes les sauvegardes de journaux.<br /><br /> Pour ignorer le plan de récupération suggéré, vous pouvez modifier les sélections dans la grille. Les sauvegardes qui dépendent d'une sauvegarde désélectionnée sont automatiquement désélectionnées.<br /><br /> Les cases à cocher sont disponibles uniquement lorsque l'option **Sélection manuelle** est activée. Vous pouvez sélectionner les jeux de sauvegarde à restaurer.<br /><br /> Quand la case **Sélection manuelle** est cochée, l’exactitude du plan de restauration est vérifiée à chacune de ses modifications. Si la séquence des sauvegardes est incorrecte, un message d'erreur s'affiche.|**Restaurer** : <br />                          Les cases à cocher sélectionnées correspondent aux jeux de sauvegarde à restaurer.<br /><br /> **Name** : <br />                          Nom du jeu de sauvegarde.<br /><br /> **Composant** : Composant sauvegardé : **Base de données**, **Fichier**, ou **\<blank>** (pour les journaux des transactions).<br /><br /> **Type** : Type de sauvegarde : **Complète**, **Différentielle** ou **Journal des transactions**.<br /><br /> **Serveur** : Nom de l’instance [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui a effectué l’opération de sauvegarde.<br /><br /> **Base de données** : <br />                          Nom de la base de données impliquée dans la sauvegarde.<br /><br /> **Position** : La position du jeu de sauvegarde dans le volume.<br /><br /> **Premier NSE**: <br />                          Numéro séquentiel dans le journal correspondant à la première transaction dans le jeu de sauvegarde. Vide pour les sauvegardes de fichiers.<br /><br /> **Dernier NSE**: <br />                          Numéro séquentiel dans le journal correspondant à la dernière transaction dans le jeu de sauvegarde. Vide pour les sauvegardes de fichiers.<br /><br /> **NSE du point de contrôle**: <br />                          Numéro séquentiel dans le journal du point de contrôle le plus récent au moment où la sauvegarde a été créée.<br /><br /> **Tous les NSE**: <br />                          Numéro séquentiel dans le journal de la sauvegarde complète de la base de données la plus récente.<br /><br /> **Date de début**: <br />                          Date et heure de lancement de l'opération de sauvegarde, présentée conformément aux paramètres régionaux du client.<br /><br /> **Date de fin**: <br />                          Date et heure de fin de l'opération de sauvegarde, exprimée d'après les paramètres régionaux du client.<br /><br /> **Size** : <br />                          Taille du jeu de sauvegarde, exprimée en octets.<br /><br /> **Nom d’utilisateur** : <br />                          Nom de l’utilisateur qui a effectué l’opération de sauvegarde.<br /><br /> **Expiration**: <br />                          La date et l'heure d'expiration du jeu de sauvegarde.|  
|**Vérifier les supports de sauvegarde**|Appelle une instruction RESTORE VERIFY_ONLY sur les jeux de sauvegarde sélectionnés.<br /><br /> Remarque : La vérification est une opération longue : vous pouvez suivre sa progression ou l’annuler en utilisant le Moniteur d’avancement dans l’infrastructure de boîte de dialogue.<br /><br /> Le bouton vous permet de vérifier l’intégrité des fichiers de sauvegarde sélectionnés avant de les restaurer.<br /><br /> Lors de la vérification de l'intégrité des jeux de sauvegarde, l'état d'avancement fourni en bas à gauche de la boîte de dialogue n'indique plus « Exécution », mais « Vérification ».||  
  
## <a name="compatibility-support"></a>Prise en charge de la compatibilité  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez restaurer une base de données utilisateur à partir d'une sauvegarde de base de données créée à l'aide de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure. Les sauvegardes des bases de données **master**, **model** et **msdb** créées avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ne peuvent pas être restaurées par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Par ailleurs, les sauvegardes créées dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne peuvent pas être restaurées par les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilise un chemin d'accès par défaut différent de celui des versions précédentes. Pour restaurer une base de données créée à l’emplacement par défaut d’une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser l’option MOVE.  
  
 Après avoir restauré une base de données de version antérieure dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la base de données est automatiquement mise à niveau. En général, la base de données est immédiatement disponible. Toutefois si une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] comprend des index de recherche en texte intégral, la mise à niveau les importe, les réinitialise ou les reconstruit, en fonction du paramètre de la propriété de serveur **Option de mise à niveau du catalogue de texte intégral** . Si l’option de mise à niveau a la valeur **Importer** ou **Reconstruire**, les index de recherche en texte intégral ne sont pas disponibles pendant la mise à niveau. Selon le volume de données indexé, l’importation peut prendre plusieurs heures et la reconstruction peut durer jusqu’à dix fois plus longtemps. Notez également que quand l’option de mise à niveau est **Importer**, si un catalogue de texte intégral n’est pas disponible, les index de recherche en texte intégral associés sont reconstruits.  
  
## <a name="restoring-from-an-encrypted-backup"></a>Restauration d'une sauvegarde chiffrée  
 La restauration nécessite que le certificat ou la clé asymétrique qui a servi à créer la sauvegarde soit disponible sur l’instance sur laquelle vous effectuez la restauration. Le compte qui effectue la restauration doit avoir l'autorisation **VIEW DEFINITIONS** sur le certificat ou la clé asymétrique. Ne renouvelez pas ou ne mettez pas à jour les certificats utilisés pour chiffrer la sauvegarde.  
  
## <a name="restoring-from-microsoft-azure-storage"></a>Restauration à partir de Microsoft Azure Storage  
Sélectionnez **URL** dans la liste déroulante **Type de support de sauvegarde** dans la boîte de dialogue **Sélectionner les unités de sauvegarde** .  Ensuite, sélectionnez **Ajouter** pour ouvrir la boîte de dialogue **Sélectionner un emplacement de fichier de sauvegarde**. Sélectionnez des informations d’identification SQL Server existantes et un conteneur de stockage Azure. Ajoutez un nouveau conteneur de stockage Azure avec une signature d’accès partagé, ou générez une signature d’accès partagé et des informations d’identification SQL Server pour un conteneur de stockage existant. Une fois que vous vous êtes connecté au compte de stockage, les fichiers de sauvegarde s’affichent dans la boîte de dialogue **Localiser le fichier de sauvegarde dans Microsoft Azure** , où vous sélectionnez le fichier à utiliser pour la restauration.  Voir aussi [Se connecter à un abonnement Microsoft Azure](../../relational-databases/backup-restore/connect-to-a-microsoft-azure-subscription.md).
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Restaurer une sauvegarde à partir d’une unité &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-backup-from-a-device-sql-server.md)   
 [Restaurer une base de données jusqu’à une transaction marquée &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)   
 [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)   
 [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [Arguments RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)   
 [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)  
  
  
