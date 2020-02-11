---
title: Sauvegarde et restauration
description: Décrit le fonctionnement de la sauvegarde et de la restauration des données pour les Data Warehouse parallèles (PDW). Les opérations de sauvegarde et de restauration sont utilisées pour la récupération d’urgence. La sauvegarde et la restauration peuvent également être utilisées pour copier une base de données d’une appliance vers une autre.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 01/19/2019
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 75399480879623a39da542c68f036389c645f6ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401349"
---
# <a name="backup-and-restore"></a>Sauvegarde et restauration

Décrit le fonctionnement de la sauvegarde et de la restauration des données pour les Data Warehouse parallèles (PDW). Les opérations de sauvegarde et de restauration sont utilisées pour la récupération d’urgence. La sauvegarde et la restauration peuvent également être utilisées pour copier une base de données d’une appliance vers une autre.  
    
## <a name="BackupRestoreBasics"></a>Notions de base de la sauvegarde et de la restauration

Une *sauvegarde de base de données* PDW est une copie d’une base de données d’appliance, stockée dans un format afin de pouvoir être utilisée pour restaurer la base de données d’origine sur un appareil.  
  
Une sauvegarde de base de données PDW est créée avec l’instruction t-SQL [Backup database](../t-sql/statements/backup-database-parallel-data-warehouse.md) et mise en forme pour une utilisation avec l’instruction [Restore Database](../t-sql/statements/restore-database-parallel-data-warehouse.md) . Il est inutilisable à d’autres fins. La sauvegarde ne peut être restaurée que sur une appliance ayant le même nombre ou un plus grand nombre de nœuds de calcul.  
  
<!-- MISSING LINKS
The [master database](master-database.md) is a SMP SQL Server database. It is backed up with the BACKUP DATABASE statement. To restore master, use the [Restore the Master Database](configuration-manager-restore-master-database.md) page of the Configuration Manager tool.  
-->
  
PDW utilise SQL Server technologie de sauvegarde pour sauvegarder et restaurer des bases de données d’appliances. SQL Server options de sauvegarde sont préconfigurées pour utiliser la compression de la sauvegarde. Vous ne pouvez pas définir des options de sauvegarde comme la compression, la somme de contrôle, la taille des blocs ou le nombre de tampons.  
  
Les sauvegardes de base de données sont stockées sur un ou plusieurs serveurs de sauvegarde, qui existent dans votre propre réseau client.  PDW écrit une sauvegarde de base de données utilisateur en parallèle directement à partir des nœuds de calcul sur un serveur de sauvegarde et restaure une sauvegarde de base de données utilisateur en parallèle directement à partir du serveur de sauvegarde vers les nœuds de calcul.  
  
Les sauvegardes sont stockées sur le serveur de sauvegarde sous la forme d’un ensemble de fichiers dans le système de fichiers Windows. Une sauvegarde de base de données PDW peut uniquement être restaurée sur PDW. Toutefois, vous pouvez archiver des sauvegardes de base de données à partir du serveur de sauvegarde vers un autre emplacement à l’aide des processus de sauvegarde de fichiers Windows standard. Pour plus d’informations sur les serveurs de sauvegarde, consultez [acquérir et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md).  
  
## <a name="BackupTypes"></a>Types de sauvegardes de base de données

Il existe deux types de données qui nécessitent une sauvegarde : les bases de données utilisateur et les bases de données système (par exemple, la base de données Master). PDW ne sauvegarde pas le journal des transactions.  
  
Une sauvegarde complète de base de données est une sauvegarde d’une base de données PDW entière. Il s’agit du type de sauvegarde par défaut. Une sauvegarde complète d’une base de données utilisateur comprend les utilisateurs de base de données et les rôles de base de données. Une sauvegarde de Master comprend des connexions.  
  
Une sauvegarde différentielle contient toutes les modifications apportées depuis la dernière sauvegarde complète. Généralement, une sauvegarde différentielle prend moins de temps qu’une sauvegarde complète et peut être effectuée plus souvent. Lorsque plusieurs sauvegardes différentielles sont basées sur la même sauvegarde complète, chaque différentielle comprend toutes les modifications de l’écart précédent.  
  
Par exemple, vous pouvez créer une sauvegarde complète hebdomadaire et une sauvegarde différentielle quotidiennement. Pour restaurer la base de données utilisateur, vous devez restaurer la sauvegarde complète plus la dernière différentielle (le cas échéant).  
  
Une sauvegarde différentielle est uniquement prise en charge pour les bases de données utilisateur. Une sauvegarde de Master est toujours une sauvegarde complète.  
  
Pour sauvegarder l’ensemble de l’appliance, vous devez effectuer une sauvegarde de toutes les bases de données utilisateur et une sauvegarde de la base de données Master.  
  
## <a name="BackupProc"></a>Processus de sauvegarde de base de données

Le diagramme suivant montre le déroulement des données lors d’une sauvegarde de base de données.  
  
![Processus de sauvegarde PDW](media/backup-process.png "Processus de sauvegarde PDW")  
  
Le processus de sauvegarde fonctionne comme suit :  
  
1.  L’utilisateur soumet une instruction TSQL BACKUP DATABASE au nœud de contrôle.  
  
    -   La sauvegarde est une sauvegarde complète ou différentielle.  
  
2.  Pour les bases de données utilisateur, le nœud de contrôle (moteur MPP) crée un plan de requête distribuée pour effectuer une sauvegarde de base de données parallèle.  
  
3.  Chaque nœud impliqué dans la sauvegarde copie son fichier de sauvegarde sur le serveur de sauvegarde à l’aide de la fonctionnalité de sauvegarde SQL Server.  
  
    -   Chaque nœud impliqué copie un fichier de sauvegarde sur le serveur de sauvegarde.  
  
    -   La sauvegarde de base de données utilisateur (complète ou différentielle) comprend une sauvegarde de la partie de la base de données stockée sur chaque nœud de calcul, ainsi qu’une sauvegarde des utilisateurs et des rôles de base de données de la base de données.  
  
4.  L’appliance effectue la sauvegarde en parallèle à l’aide du réseau InfiniBand.  
  
    -   PDW effectue chaque sauvegarde complète et différentielle en parallèle. Toutefois, les sauvegardes de plusieurs bases de données ne sont pas exécutées simultanément. Chaque demande de sauvegarde doit attendre la fin des sauvegardes soumises précédemment.  
  
    -   Une sauvegarde de la base de données Master sauvegarde uniquement les données du nœud de contrôle. Ce type de sauvegarde est exécuté en série.  
  
5.  Une sauvegarde de base de données PDW est un groupe de fichiers stockés dans un répertoire qui réside dans l’appliance. Le nom du répertoire est spécifié sous la forme d’un chemin d’accès réseau et d’un nom de répertoire. Le répertoire ne peut pas être un chemin d’accès local et ne peut pas se trouver sur l’appliance.  
  
6.  Une fois la sauvegarde terminée, vous pouvez utiliser le système de fichiers Windows pour copier le répertoire de sauvegarde dans un autre emplacement, si vous le souhaitez.  
  
    -   Une sauvegarde ne peut être restaurée que sur une appliance PDW qui possède un nombre égal ou supérieur de nœuds de calcul.  
  
    -   Vous ne pouvez pas modifier le nom de la sauvegarde avant d’effectuer une restauration. Le nom du répertoire de sauvegarde doit correspondre au nom du nom d’origine de la sauvegarde. Le nom d’origine de la sauvegarde se trouve dans le fichier backup. xml dans le répertoire de sauvegarde. Pour restaurer une base de données avec un nom différent, vous pouvez spécifier le nouveau nom dans la commande Restore. Par exemple : `RESTORE DATABASE MyDB1 FROM DISK = ꞌ\\10.192.10.10\backups\MyDB2ꞌ`.  
  
## <a name="RestoreModes"></a>Modes de restauration de base de données

Une restauration de base de données complète recrée la base de données PDW en utilisant les données de la sauvegarde de base de données. La restauration de la base de données est effectuée en commençant par restaurer une sauvegarde complète, puis en restaurant éventuellement une sauvegarde différentielle. La restauration de la base de données comprend les utilisateurs de base de données et les rôles de base de données.  
  
Une restauration d’en-tête uniquement retourne les informations d’en-tête d’une base de données. Il ne restaure pas les données sur l’appliance.  
  
Une restauration de l’appliance est une restauration de l’ensemble de l’appliance. Cela comprend la restauration de toutes les bases de données utilisateur et de la base de données Master.  
  
## <a name="RestoreProc"></a>Processus de restauration

Le diagramme suivant montre le déroulement des données lors d’une restauration de base de données.  
  
![Processus de restauration](media/restore-process.png "Processus de restauration")  
  
## <a name="restoring-to-an-appliance-with-the-same-number-of-compute-nodes"></a>Restauration sur une appliance avec le même nombre de nœuds de calcul * *  
  
Lors de la restauration de données, l’appliance détecte le nombre de nœuds de calcul sur l’appliance source et l’appliance de destination. Si les deux Appliances ont un nombre égal de nœuds de calcul, le processus de restauration fonctionne comme suit :  
  
1.  La sauvegarde de base de données à restaurer est disponible sur un partage de fichiers Windows sur un serveur de sauvegarde non-appareil. Pour de meilleures performances, ce serveur est connecté au réseau de l’appliance InfiniBand.  
  
2.  L’utilisateur soumet une instruction TSQL [Restore Database](../t-sql/statements/restore-database-parallel-data-warehouse.md) au nœud de contrôle.  
  
    -   La restauration est une restauration complète ou une restauration d’en-tête. La restauration complète restaure une sauvegarde complète, puis restaure éventuellement une sauvegarde différentielle.  
  
3.  Le nœud de contrôle (moteur MPP) crée un plan de requête distribuée pour effectuer une restauration de base de données parallèle.  
  
    -   SQL ServerPDW effectue la restauration d’une base de données utilisateur en parallèle. Toutefois, les sauvegardes et restaurations de plusieurs bases de données ne sont pas exécutées simultanément. Le moteur MPP place chaque instruction RESTORE dans une file d’attente ; il doit attendre la fin des demandes de sauvegarde et de restauration précédemment envoyées.  
  
    -   Une restauration de la base de données Master restaure uniquement les données du nœud de contrôle ; la restauration est effectuée en série.  
  
    -   Une restauration des informations d’en-tête est une opération rapide qui ne restaure pas de données sur les nœuds de calcul ou de contrôle. Au lieu de cela, le nœud de contrôle retourne les résultats en tant que sortie de la requête.  
  
4.  Les fichiers de sauvegarde sont copiés vers les nœuds de calcul appropriés en parallèle, généralement sur le réseau de l’appliance InfiniBand.  
  
5.  Chaque nœud de calcul restaure sa partie de la base de données utilisateur. Si l’une des restaurations ne se termine pas correctement, toutes les bases de données sont supprimées et la restauration échoue.  
  
## <a name="restoring-to-an-appliance-with-a-larger-number-of-compute-nodes"></a>Restauration dans une appliance dotée d’un plus grand nombre de nœuds de calcul  
  
Le fait de restaurer une sauvegarde dans une appliance dotée d’un plus grand nombre de nœuds de calcul a pour effet d’accroître la taille de la base de données allouée de façon proportionnelle au nombre de nœuds de calcul.  
  
Par exemple, lors de la restauration d’une base de données 60 Go à partir d’une appliance à 2 nœuds (30 Go par nœud) vers une appliance à 6 nœuds, SQL Server PDW crée une base de données de 180 Go (6 nœuds avec 30 Go par nœud) sur l’appliance à 6 nœuds. SQL Server PDW restaure initialement la base de données à 2 nœuds pour qu’elle corresponde à la configuration source, puis redistribue les données sur les 6 nœuds.  
  
Après la redistribution, chaque nœud de calcul contiendra moins de données réelles et plus d’espace libre que chaque nœud de calcul sur le plus petit appareil source. Profitez de l’espace supplémentaire pour ajouter davantage de données à la base de données. Si la taille de la base de données restaurée est supérieure à celle dont vous avez besoin, vous pouvez utiliser [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) pour réduire la taille des fichiers de base de données.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Tâche de sauvegarde et de restauration|Description|  
|---------------------------|---------------|  
|Préparez un serveur en tant que serveur de sauvegarde.|[Obtenir et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md)|  
|Sauvegardez une base de données.|[BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)|  
|Restaure une base de données.|[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)|    

<!-- MISSING LINKS

|Create a disaster recovery plan.|[Create a Disaster Recovery Plan](create-disaster-recovery-plan.md)|
|Restore the master database.|To restore the master database, use the [Restore the master database](configuration-manager-restore-master-database.md) page in the Configuration Manager tool.| 
|Copy a database from one appliance to another appliance.|[Copy a PDW database to another appliance](copy-pdw-database-to-another-appliance.md).|  
|Monitor backups and restores.|[Monitor backups and restores](monitor-backup-and-restore.md)|  

-->
