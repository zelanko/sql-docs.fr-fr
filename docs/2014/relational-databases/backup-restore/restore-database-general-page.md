---
title: Restaurer la base de données (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.restoredb.general.f1
ms.assetid: 160cf58c-b06a-475f-9a69-2b051e5767ab
caps.latest.revision: 85
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f310d762ca8a8d116b3accc618532b772eef8c26
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143758"
---
# <a name="restore-database-general-page"></a>Restaurer la base de données (page Général)
  Utilisez la page **Général** pour spécifier des informations sur les bases de données cible et source dans le cadre d’une opération de restauration de base de données.  
  
 **Pour utiliser SQL Server Management Studio pour restaurer une sauvegarde de base de données**  
  
-   [Restaurer une sauvegarde de base de données &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  Lorsque vous spécifiez une tâche de restauration à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez générer correspondant [!INCLUDE[tsql](../../includes/tsql-md.md)] [restaurer](/sql/t-sql/statements/restore-statements-transact-sql) script en cliquant sur **Script** , puis en sélectionnant une destination pour le script.  
  
## <a name="permissions"></a>Autorisations  
 Si la base de données restaurée n'existe pas, l'utilisateur doit posséder les autorisations CREATE DATABASE afin de pouvoir exécuter RESTORE. Si la base de données existe, les autorisations RESTORE reviennent par défaut aux membres des rôles serveur fixes **sysadmin** et **dbcreator** et au propriétaire (**dbo**) de la base de données.  
  
 Les autorisations RESTORE sont attribuées aux rôles dont les informations d'appartenance sont toujours immédiatement accessibles à partir du serveur. Étant donné que l’appartenance au rôle de base de données fixe ne peut être contrôlée que quand la base de données est accessible et non endommagée, ce qui n’est pas toujours le cas lorsque RESTORE est exécuté, les membres du rôle de base de données fixe **db_owner** ne détiennent pas d’autorisations RESTORE.  
  
 La restauration depuis une sauvegarde chiffrée requiert `VIEW DEFINITION` des autorisations pour le certificat ou la clé asymétrique utilisée pour chiffrer pendant la sauvegarde.  
  
## <a name="options"></a>Options  
  
### <a name="source"></a>Source  
 Les options du volet **Restaurer à partir de**identifient l’emplacement des jeux de sauvegarde pour la base de données ainsi que les jeux de sauvegarde que vous souhaitez restaurer.  
  
|Terme|Définition|  
|----------|----------------|  
|**Sauvegarde de la base de données**|Sélectionnez la base de données à restaurer dans la liste déroulante. La liste contient uniquement les bases de données qui ont été sauvegardées selon l'historique de sauvegarde **msdb** .|  
|**Unité**|Sélectionnez les unités de sauvegarde logiques ou physiques (bandes, URL ou fichiers) qui contiennent la ou les sauvegardes à restaurer. Cela est requis si la sauvegarde de la base de données a été effectuée sur une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Pour sélectionner une ou plusieurs unités de sauvegarde logiques ou physiques, cliquez sur le bouton Parcourir afin d'ouvrir la boîte de dialogue **Sélectionner les unités de sauvegarde** . Dans cette boîte de dialogue, vous pouvez sélectionner jusqu'à 64 unités appartenant au même support de sauvegarde. Les lecteurs de bande doivent être connectés physiquement à l'ordinateur qui exécute l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un fichier de sauvegarde peut se trouver sur une unité de disque locale ou distante. Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md). Vous pouvez également sélectionner **URL** comme type de périphérique pour sauvegarder les fichiers stockés dans le stockage Windows Azure.<br /><br /> Quand vous fermez la boîte de dialogue **Sélectionner les unités de sauvegarde** , l’unité sélectionnée s’affiche sous forme de valeurs accessibles en lecture seule dans la liste **Unité** .|  
|**Sauvegarde de la base de données**|Sélectionnez dans la liste déroulante le nom de la base de données depuis laquelle les sauvegardes doivent être restaurées.<br /><br /> Remarque : cette liste n’est disponible que lorsque l’option **Unité** est sélectionnée. Seules les bases de données qui ont des copies de sauvegarde sur les unités sélectionnées sont disponibles.|  
  
### <a name="destination"></a>Destination  
 Les options du volet **Restaurer sur** identifient la base de données et le point de restauration.  
  
|Terme|Définition|  
|----------|----------------|  
|**Sauvegarde de la base de données**|Entrez la base de données à restaurer dans la liste. Vous pouvez entrer une nouvelle base de données ou choisir une base de données existante dans la liste déroulante. La liste contient toutes les bases de données sur le serveur, à l'exception des bases de données système **master** et **tempdb**.<br /><br /> Remarque : Pour restaurer une sauvegarde protégée par mot de passe, vous devez utiliser l’instruction [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) .|  
|**Restaurer sur**|Par défaut, la zone **Restaurer sur** a la valeur « Dernière sauvegarde effectuée ». Vous pouvez également cliquer sur **Chronologie** pour ouvrir la boîte de dialogue **Chronologie de sauvegarde** , qui affiche l'historique de sauvegarde de la base de données sous forme de chronologie. Cliquez sur **chronologie** pour désigner un spécifique `datetime` pour lequel vous souhaitez restaurer la base de données. La base de données est ensuite restaurée dans l'état où elle se trouvait aux date et heure spécifiées. Consultez [Backup Timeline](backup-timeline.md).|  
  
### <a name="restore-plan"></a>Plan de restauration  
  
|Terme|Définition|  
|----------|----------------|  
|**Jeux de sauvegarde à restaurer**|Affiche les jeux de sauvegarde disponibles pour l'emplacement indiqué. Chaque jeu de sauvegarde (résultat d'une opération de sauvegarde unique) est réparti sur toutes les unités du support de sauvegarde. Par défaut, un plan de récupération est proposé pour accomplir l'opération de restauration basée sur la sélection des jeux de sauvegarde requis. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise l'historique de sauvegarde dans **msdb** pour identifier les sauvegardes nécessaires à la restauration d'une base de données et crée un plan de restauration. Par exemple, pour une restauration de base de données, le plan de restauration sélectionne la sauvegarde de base de données complète la plus récente, suivie de la sauvegarde de base de données différentielle suivante la plus récente, le cas échéant. Avec le mode de récupération complète, le plan de restauration sélectionne ensuite toutes les sauvegardes de journaux suivantes.<br /><br /> Pour ignorer le plan de récupération suggéré, vous pouvez modifier les sélections suivantes dans la grille. Les sauvegardes qui dépendent d'une sauvegarde désélectionnée sont automatiquement désélectionnées.<br /><br /> **Restaurer**:<br />                          Les cases à cocher sélectionnées correspondent aux jeux de sauvegarde à restaurer.<br />**Nom**: le nom du jeu de sauvegarde.<br />**Composant**: le composant sauvegardé : **base de données**, **fichier**, ou  **\<vide >** (pour les journaux des transactions).<br />**Type**: type de sauvegarde effectué : **Complète**, **Différentielle**ou **Journal des transactions**.<br />**Serveur**: nom de l’instance [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui a effectué l’opération de sauvegarde.<br />**Base de données**: le nom de la base de données impliquée dans l’opération de sauvegarde.<br />**Position**: position du jeu de sauvegarde dans le volume.<br />**Premier NSE**: le numéro de séquence de journal de la première transaction dans le jeu de sauvegarde. Vide pour les sauvegardes de fichiers.<br />**LSN de dernière**: le numéro de séquence de journal de la dernière transaction dans le jeu de sauvegarde. Vide pour les sauvegardes de fichiers.<br />**Point de contrôle LSN**: le numéro de séquence du journal (LSN) du contrôle plus récent au moment de la création de la sauvegarde.<br />**Tous les NSE**: le numéro de séquence de journal de la dernière sauvegarde de base de données complète.<br />**Date de début**: la date et l’heure de début de l’opération de sauvegarde, présentée dans les paramètres régionaux du client.<br />**Date de fin**: la date et l’heure de fin de l’opération de sauvegarde, présentée dans les paramètres régionaux du client.<br />**Taille**: la taille de la sauvegarde est définie en octets.<br />**Nom d’utilisateur**: le nom de l’utilisateur qui a effectué l’opération de sauvegarde.<br /><br /> **Expiration**: la date et l’heure d’expiration du jeu de sauvegarde.<br /><br /> Les cases à cocher sont disponibles uniquement lorsque l'option **Sélection manuelle** est activée. Cela vous permet de sélectionner les jeux de sauvegarde à restaurer.<br /><br /> Lorsque l'option **Sélection manuelle** est activée, l'exactitude du plan de restauration est vérifiée à chacune de ses modifications. Si la séquence des sauvegardes est incorrecte, un message d'erreur s'affiche.|  
|**Vérifier les supports de sauvegarde**|Appelle une instruction RESTORE VERIFY_ONLY sur les jeux de sauvegarde sélectionnés.<br /><br /> Remarque : cette opération est longue, et sa progression peut être suivie et annulée à l’aide du Moniteur d’avancement de l’Infrastructure de boîte de dialogue.<br /><br /> Ce bouton vous permet de vérifier l'intégrité des fichiers de sauvegarde sélectionnés avant de les restaurer.<br /><br /> Lors de la vérification de l'intégrité des jeux de sauvegarde, l'état d'avancement fourni en bas à gauche de la boîte de dialogue n'indique plus « Exécution », mais « Vérification ».|  
  
## <a name="compatibility-support"></a>Prise en charge de la compatibilité  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez restaurer une base de données utilisateur à partir d'une sauvegarde de base de données créée à l'aide de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure. Cependant, les sauvegardes des bases de données **master**, **model** et **msdb** créées avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] via [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ne peuvent pas être restaurées par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Par ailleurs, les sauvegardes créées dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne peuvent pas être restaurées par les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilise un chemin d'accès par défaut différent de celui des versions précédentes. Par conséquent, pour restaurer une base de données créée à l'emplacement par défaut d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser l'option MOVE.  
  
 Après avoir restauré une base de données de version antérieure dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la base de données est automatiquement mise à niveau. En général, la base de données est immédiatement disponible. Toutefois si une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] comprend des index de recherche en texte intégral, la mise à niveau les importe, les réinitialise ou les reconstruit, en fonction du paramètre de la propriété de serveur **Option de mise à niveau du catalogue de texte intégral** . Si l’option de mise à niveau a la valeur **Importer** ou **Reconstruire**, les index de recherche en texte intégral ne seront pas disponibles pendant la mise à niveau. Selon le volume de données indexé, l'importation peut prendre plusieurs heures et la reconstruction jusqu'à dix fois plus longtemps. Notez également que quand l’option de mise à niveau est **Importer**, si un catalogue de texte intégral n’est pas disponible, les index de recherche en texte intégral associés sont reconstruits.  
  
## <a name="restoring-from-an-encrypted-backup"></a>Restauration d'une sauvegarde chiffrée  
 La restauration nécessite que le certificat ou la clé asymétrique qui a servi à créer la sauvegarde soit disponible sur l'instance sur laquelle vous effectuez la restauration. Le compte qui effectue la restauration doit avoir `VIEW DEFINITIONS` sur le certificat ou une clé asymétrique. Les certificats utilisés pour chiffrer la sauvegarde ne doivent pas être renouvelés ou mis à jour.  
  
## <a name="restoring-from-windows-azure-storage"></a>Restauration à partir du stockage Windows Azure  
 Lorsque vous restaurez une sauvegarde stockée dans le stockage Windows Azure, une nouvelle option d'unité de sauvegarde vous est proposée dans l'interface de restauration : l'option**URL** dans la boîte de dialogue **Sélectionner les unités de sauvegarde** . Lorsque vous cliquez sur **Ajouter**, la boîte de dialogue **Se connecter à Windows Azure** s'affiche et vous permet de spécifier les informations d'identification SQL utilisées pour authentifier le compte de stockage.  Une fois que vous vous êtes connecté au compte de stockage, les fichiers de sauvegarde s'affichent dans la boîte de dialogue **Localiser le fichier de sauvegarde dans Windows Azure** où vous sélectionnez le fichier à utiliser pour la restauration.  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Restaurer une sauvegarde à partir d’une unité &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)   
 [Restaurer une base de données jusqu’à une transaction marquée &#40;SQL Server Management Studio&#41;](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)   
 [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [Arguments RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)   
 [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)  
  
  
