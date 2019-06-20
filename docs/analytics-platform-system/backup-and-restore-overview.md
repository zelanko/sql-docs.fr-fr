---
title: Sauvegarde et restauration - Parallel Data Warehouse | Microsoft Docs
description: Décrit comment données de sauvegarde et de restauration pour Parallel Data Warehouse (PDW). Opérations de sauvegarde et de restauration sont utilisées pour la récupération d’urgence. Sauvegarde et restauration peuvent également être utilisés pour copier une base de données d’une appliance vers une autre appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 01/19/2019
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0b95d18eb38bbe0012235304747ca80b3dc19a79
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200960"
---
# <a name="backup-and-restore"></a>Sauvegarde et restauration

Décrit comment données de sauvegarde et de restauration pour Parallel Data Warehouse (PDW). Opérations de sauvegarde et de restauration sont utilisées pour la récupération d’urgence. Sauvegarde et restauration peuvent également être utilisés pour copier une base de données d’une appliance vers une autre appliance.  
    
## <a name="BackupRestoreBasics"></a>Principes élémentaires de sauvegarde et restauration

Un entrepôt PDW *sauvegarde de base de données* est une copie d’une base de données d’appliance, stockée dans un format afin qu’il peut être utilisé pour restaurer la base de données d’origine vers un appareil.  
  
Une sauvegarde de base de données PDW est créée avec le [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md) instruction t-sql et mis en forme pour une utilisation avec le [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) instruction ; il est inutilisable à d’autres fins. La sauvegarde peut uniquement être restaurée vers un appareil avec le même nombre ou un plus grand nombre de nœuds de calcul.  
  
<!-- MISSING LINKS
The [master database](master-database.md) is a SMP SQL Server database. It is backed up with the BACKUP DATABASE statement. To restore master, use the [Restore the Master Database](configuration-manager-restore-master-database.md) page of the Configuration Manager tool.  
-->
  
PDW utilise la technologie de sauvegarde de SQL Server pour sauvegarder et restaurer des bases de données appliance. Options de sauvegarde de SQL Server sont préconfigurées pour utiliser la compression de sauvegarde. Vous ne pouvez pas définir des options de sauvegarde comme la compression, la somme de contrôle, la taille des blocs ou le nombre de tampons.  
  
Sauvegardes de base de données sont stockés sur un ou plusieurs serveurs de sauvegarde, qui existe dans votre propre réseau du client.  PDW écrit une sauvegarde de base de données utilisateur, en parallèle, directement à partir des nœuds de calcul à un seul serveur de sauvegarde et restaure une sauvegarde de base de données utilisateur en parallèle directement depuis le serveur de sauvegarde pour les nœuds de calcul.  
  
Sauvegardes sont stockées sur le serveur de sauvegarde en tant qu’ensemble de fichiers dans le système de fichiers Windows. Une sauvegarde de base de données PDW peut uniquement être restaurée à PDW. Toutefois, vous pouvez archiver les sauvegardes de base de données à partir du serveur de sauvegarde vers un autre emplacement à l’aide du processus de sauvegarde de fichier de Windows standards. Pour plus d’informations sur les serveurs de sauvegarde, consultez [Acquire et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md).  
  
## <a name="BackupTypes"></a>Types de sauvegarde de base de données

Il existe deux types de données qui nécessitent une sauvegarde : bases de données utilisateur et les bases de données système (par exemple, la base de données master). PDW ne sauvegarde pas le journal des transactions.  
  
Une sauvegarde de base de données complète est une sauvegarde d’une base de données entière PDW. Il s’agit du type de sauvegarde par défaut. Une sauvegarde complète de base de données utilisateur inclut la base de données et les rôles de base de données. Une sauvegarde de master comprend les connexions.  
  
Une sauvegarde différentielle contient toutes les modifications depuis la dernière sauvegarde complète. Généralement, une sauvegarde différentielle prend moins de temps qu’une sauvegarde complète et peut être effectuée plus souvent. Quand plusieurs sauvegardes différentielles sont basées sur la même sauvegarde complète, chaque sauvegarde différentielle inclut toutes les modifications dans la sauvegarde différentielle précédente.  
  
Par exemple, vous pouvez créer une sauvegarde complète hebdomadaire et une sauvegarde différentielle quotidienne. Pour restaurer la base de données utilisateur, de la sauvegarde complète ainsi que la dernière sauvegarde différentielle (le cas échéant) doit être restaurée.  
  
Une sauvegarde différentielle est uniquement pris en charge pour les bases de données utilisateur. Une sauvegarde du serveur principal est toujours une sauvegarde complète.  
  
Pour sauvegarder l’application entière, vous devez effectuer une sauvegarde de toutes les bases de données utilisateur et une sauvegarde de la base de données master.  
  
## <a name="BackupProc"></a>Processus de sauvegarde de base de données

Le diagramme suivant illustre le flux de données lors d’une sauvegarde de base de données.  
  
![Processus de sauvegarde PDW](media/backup-process.png "les processus de sauvegarde PDW")  
  
Le processus de sauvegarde fonctionne comme suit :  
  
1.  Utilisateur soumet une instruction tsql de base de données de sauvegarde au nœud de contrôle.  
  
    -   La sauvegarde est une sauvegarde complète ou différentielle.  
  
2.  Pour les bases de données utilisateur, le nœud de contrôle (moteur MPP) crée un plan de requête distribuée pour effectuer une sauvegarde de base de données parallèle.  
  
3.  Chaque nœud impliqué dans les copies de sauvegarde son fichier de sauvegarde pour le serveur de sauvegarde à l’aide de la fonctionnalité de sauvegarde de SQL Server.  
  
    -   Chaque nœud impliqué copie un fichier de sauvegarde pour le serveur de sauvegarde.  
  
    -   La sauvegarde de base de données utilisateur (complète ou différentielle) inclut une sauvegarde de la partie de la base de données stocké sur chaque nœud de calcul et une sauvegarde des utilisateurs de base de données et des rôles de base de données.  
  
4.  La solution effectue la sauvegarde en parallèle en utilisant le réseau InfiniBand.  
  
    -   PDW exécute chaque sauvegarde complète et différentielle en parallèle. Toutefois, plusieurs sauvegardes de base de données ne s’exécutent pas simultanément. Chaque demande de sauvegarde doit attendre pour les sauvegardes précédemment soumises à la fin.  
  
    -   Une sauvegarde de la base de données master sauvegarde uniquement les données à partir du nœud de contrôle. Ce type de sauvegarde est effectué en série.  
  
5.  Une sauvegarde de base de données PDW est un groupe de fichiers stockés dans un répertoire qui se trouve en dehors de l’appliance. Le nom du répertoire est spécifié comme un nom de chemin d’accès et le répertoire réseau. Le répertoire ne peut pas être un chemin d’accès local, et il ne peut pas se trouver sur l’appliance.  
  
6.  Une fois la sauvegarde est terminée, vous pouvez utiliser le système de fichiers Windows pour copier le répertoire de sauvegarde vers un autre emplacement, si vous le souhaitez.  
  
    -   Une sauvegarde peut uniquement être restaurée vers une appliance PDW qui a un nombre supérieur ou égal de nœuds de calcul.  
  
    -   Vous ne pouvez pas modifier le nom de la sauvegarde avant d’effectuer une restauration. Le nom du répertoire de sauvegarde doit correspondre au nom du nom d’origine de la sauvegarde. Le nom d’origine de la sauvegarde se trouve dans le fichier backup.xml dans le répertoire de sauvegarde. Pour restaurer une base de données sous un nom différent, vous pouvez spécifier le nouveau nom dans la commande restore. Par exemple : `RESTORE DATABASE MyDB1 FROM DISK = ꞌ\\10.192.10.10\backups\MyDB2ꞌ`.  
  
## <a name="RestoreModes"></a>Modes de restauration de base de données

Une restauration de base de données complète permet de recréer la base de données PDW en utilisant les données dans la sauvegarde de base de données. La restauration de base de données est effectuée en restaurant tout d’abord une sauvegarde complète, puis en restaurant une sauvegarde différentielle si vous le souhaitez. La restauration de base de données inclut les utilisateurs de base de données et les rôles de base de données.  
  
Une restauration seul en-tête retourne les informations d’en-tête pour une base de données. Il ne restaure pas les données à l’appliance.  
  
Une restauration de l’appliance est une restauration de l’application entière. Cela inclut la restauration de toutes les bases de données utilisateur et la base de données master.  
  
## <a name="RestoreProc"></a>Processus de restauration

Le diagramme suivant illustre le flux de données lors d’une restauration de base de données.  
  
![Processus de restauration](media/restore-process.png "processus de restauration")  
  
## <a name="restoring-to-an-appliance-with-the-same-number-of-compute-nodes"></a>Restauration vers un appareil avec le même nombre de nœuds de calcul **  
  
Lors de la restauration des données, l’appliance détecte le nombre de nœuds de calcul sur l’appliance source et de l’appliance de destination. Si les deux appliances posséder un même nombre de nœuds de calcul, le processus de restauration fonctionne comme suit :  
  
1.  La sauvegarde de base de données à restaurer est disponible sur un partage de fichiers Windows sur un serveur de sauvegarde non-appliance. Pour de meilleures performances, ce serveur est connecté au réseau InfiniBand appliance.  
  
2.  Utilisateur soumet un [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) instruction tsql pour le nœud de contrôle.  
  
    -   La restauration est une restauration complète ou une restauration de l’en-tête. La restauration complète restaure une sauvegarde complète et éventuellement de restaurer une sauvegarde différentielle.  
  
3.  Le nœud de contrôle (moteur MPP) crée un plan de requête distribuée pour effectuer une restauration de base de données parallèle.  
  
    -   SQL ServerPDW effectue la restauration d’une base de données utilisateur en parallèle. Toutefois, plusieurs sauvegardes de base de données et des restaurations ne sont pas exécutées simultanément. Le moteur MPP place chaque instruction de restauration dans une file d’attente ; Il doit attendre la sauvegarde précédemment soumise et restaurer des demandes à terminer.  
  
    -   Une restauration de la base de données master restaure uniquement les données vers le nœud de contrôle ; la restauration est effectuée en série.  
  
    -   Une restauration des informations d’en-tête est une opération rapide et ne restaure pas les données sur les nœuds de calcul ou le contrôle. Au lieu de cela, le nœud de contrôle retourne les résultats en tant que résultat de la requête.  
  
4.  Les fichiers de sauvegarde copiés sur les nœuds de calcul corrects en parallèle, généralement sur le réseau InfiniBand appliance.  
  
5.  Chaque nœud de calcul restaure sa partie de la base de données utilisateur. Si un des restaurations ne se terminent pas correctement, toutes les bases de données sont supprimés et la restauration se termine sans succès.  
  
## <a name="restoring-to-an-appliance-with-a-larger-number-of-compute-nodes"></a>Restauration dans une appliance dotée d’un plus grand nombre de nœuds de calcul  
  
Le fait de restaurer une sauvegarde dans une appliance dotée d’un plus grand nombre de nœuds de calcul a pour effet d’accroître la taille de la base de données allouée de façon proportionnelle au nombre de nœuds de calcul.  
  
Par exemple, lorsque vous restaurez une base de données de 60 Go à partir d’une appliance de 2 nœuds (30 Go par nœud) vers une appliance à 6 nœuds, SQL Server PDW crée une base de données de 180 Go (6 nœuds avec 30 Go par nœud) sur l’appliance à 6 nœuds. SQL Server PDW commence par restaurer la base de données à 2 nœuds correspondant à la configuration de la source, puis redistribue les données aux 6 nœuds.  
  
Après la redistribution, chaque nœud de calcul contient moins de données réelles et davantage d’espace libre que chaque nœud de calcul sur l’appliance source plus petits. Profitez de l’espace supplémentaire pour ajouter davantage de données à la base de données. Si la taille de la base de données restaurée est plus volumineux que vous avez besoin, vous pouvez utiliser [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) pour réduire la taille des fichiers de base de données.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Sauvegarde et la tâche de restauration|Description|  
|---------------------------|---------------|  
|Préparer un serveur comme serveur de sauvegarde.|[Obtenir et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md)|  
|Sauvegarde une base de données.|[BASE DE DONNÉES DE SAUVEGARDE](../t-sql/statements/backup-database-parallel-data-warehouse.md)|  
|Restaurer une base de données.|[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)|    

<!-- MISSING LINKS

|Create a disaster recovery plan.|[Create a Disaster Recovery Plan](create-disaster-recovery-plan.md)|
|Restore the master database.|To restore the master database, use the [Restore the master database](configuration-manager-restore-master-database.md) page in the Configuration Manager tool.| 
|Copy a database from one appliance to another appliance.|[Copy a PDW database to another appliance](copy-pdw-database-to-another-appliance.md).|  
|Monitor backups and restores.|[Monitor backups and restores](monitor-backup-and-restore.md)|  

-->
