---
title: Base de données master | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 767d77eefe8c54fe5a3d584c670cc991b284178e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62917042"
---
# <a name="master-database"></a>Base de données master
  La base de données **master** contient l’intégralité des informations système relatives à un système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cela inclut les métadonnées relatives à l'instance, dont les comptes d'ouverture de session, les points de terminaison, les serveurs liés et les paramètres de configuration du système. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les objets système ne sont plus stockés dans la base de données **master** , mais dans la [base de données des ressources](resource-database.md). La base de données **master** enregistre également l'existence de toutes les bases de données et l'emplacement de leurs fichiers, et contient les informations d'initialisation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas démarrer si la base de données **master** n'est pas disponible.  
  
## <a name="physical-properties-of-master"></a>Propriétés physiques de la base de données master  
 Le tableau suivant énumère les valeurs de configuration initiales des données et des journaux de la base de données **master** . La taille de ces fichiers peut varier légèrement en fonction des éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Fichier|Nom logique|Nom physique|Croissance du fichier|  
|----------|------------------|-------------------|-----------------|  
|Données primaires|master|master.mdf|Croissance automatique de 10 % jusqu'à saturation du disque.|  
|Journal|mastlog|mastlog.ldf|Croissance automatique de 10 % jusqu'à un maximum de 2 téraoctets.|  
  
 Pour plus d’informations sur la manière de déplacer les données et les fichiers journaux **master** , consultez [Déplacer des bases de données système](system-databases.md).  
  
### <a name="database-options"></a>Options de base de données  
 Le tableau suivant indique la valeur par défaut pour chaque option de la base de données **master** et si cette option peut être modifiée. Pour afficher les valeurs actuelles de ces options, utilisez l'affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Option de base de données|Valeur par défaut|Peut être modifiée|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ACTIVÉ|Non|  
|ANSI_NULL_DEFAULT|OFF|Oui|  
|ANSI_NULLS|OFF|Oui|  
|ANSI_PADDING|OFF|Oui|  
|ANSI_WARNINGS|OFF|Oui|  
|ARITHABORT|OFF|Oui|  
|AUTO_CLOSE|OFF|Non|  
|AUTO_CREATE_STATISTICS|ACTIVÉ|Oui|  
|AUTO_SHRINK|OFF|Non|  
|AUTO_UPDATE_STATISTICS|ACTIVÉ|Oui|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Oui|  
|CHANGE_TRACKING|OFF|Non|  
|CONCAT_NULL_YIELDS_NULL|OFF|Oui|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Oui|  
|CURSOR_DEFAULT|GLOBAL|Oui|  
|Options de disponibilité de base de données|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Non<br /><br /> Non<br /><br /> Non|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Oui|  
|DB_CHAINING|ACTIVÉ|Non|  
|ENCRYPTION|OFF|Non|  
|NUMERIC_ROUNDABORT|OFF|Oui|  
|PAGE_VERIFY|CHECKSUM|Oui|  
|PARAMETERIZATION|SIMPLE|Oui|  
|QUOTED_IDENTIFIER|OFF|Oui|  
|READ_COMMITTED_SNAPSHOT|OFF|Non|  
|RECOVERY|SIMPLE|Oui|  
|RECURSIVE_TRIGGERS|OFF|Oui|  
|Options de Service Broker|DISABLE_BROKER|Non|  
|TRUSTWORTHY|OFF|Oui|  
  
 Pour obtenir une description de ces options de base de données, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="restrictions"></a>Restrictions  
 Les opérations suivantes ne peuvent pas être effectuées sur la base de données **master** :  
  
-   ajout de groupes de fichiers ou de fichiers ;  
  
-   Modification du classement. Le classement par défaut est le classement du serveur.  
  
-   Modification du propriétaire de la base de données. La base de données**master** appartient à **sa**.  
  
-   création d'un catalogue ou d'un index de texte intégral ;  
  
-   création de déclencheurs sur les tables système de la base de données ;  
  
-   Suppression de la base de données  
  
-   Suppression de l’utilisateur **invité** de la base de données.  
  
-   Activation de la capture des données modifiées.  
  
-   Participation à la mise en miroir de bases de données  
  
-   Suppression du groupe de fichiers primaire, du fichier de données primaire ou du fichier journal  
  
-   Changement du nom de la base de données ou du groupe de fichiers primaire  
  
-   Affectation de la valeur OFFLINE à la base de données.  
  
-   Affectation de la valeur READ_ONLY à la base de données ou au groupe de fichiers primaire  
  
## <a name="recommendations"></a>Recommandations  
 Lorsque vous travaillez avec la base de données **master** , tenez compte des recommandations suivantes :  
  
-   Ayez toujours une sauvegarde actuelle de la base de données **master** .  
  
-   Sauvegardez la base de données **master** dès que possible après les opérations suivantes :  
  
    -   création, modification ou suppression d'une base de données quelconque ;  
  
    -   modification des valeurs de configuration de la base de données ou du serveur ;  
  
    -   modification ou ajout de comptes d'ouverture de session.  
  
-   Ne créez pas d'objets utilisateur dans la base de données **master**. Si vous en créez, il faut sauvegarder la base de données **master** plus souvent.  
  
-   N'attribuez pas la valeur ON à l'option TRUSTWORTHY pour la base de données **master** .  
  
## <a name="what-to-do-if-master-becomes-unusable"></a>Procédure à suivre si la base de données master devient inutilisable  
 Si la base de données **master** devient inutilisable, vous pouvez la ramener à un état utilisable de deux manières :  
  
-   en restaurant la base de données **master** depuis une sauvegarde actuelle.  
  
     Si vous pouvez démarrer l'instance du serveur, vous pouvez restaurer la base de données **master** depuis une sauvegarde complète. Pour plus d’informations, consultez [Restaurer la base de données MASTER &#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md).  
  
-   Recréez complètement la base de données **master** .  
  
     Si la base de données **master** est gravement endommagée et ne vous permet pas de démarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez recréer la base de données **master**. Pour plus d’informations, consultez [Reconstruire des bases de données système](rebuild-system-databases.md).  
  
    > [!IMPORTANT]  
    >  Lorsque vous recréez la base de données **master** , vous recréez toutes les bases de données système.  
  
## <a name="related-content"></a>Contenu associé  
 [Reconstruire des bases de données système](rebuild-system-databases.md)  
  
 [Bases de données système](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Déplacer des fichiers de bases de données](move-database-files.md)  
  
  
