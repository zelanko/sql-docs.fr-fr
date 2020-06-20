---
title: model, base de données | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- template databases [SQL Server]
- model database [SQL Server], about model databases
- model database [SQL Server]
ms.assetid: 4e4f739b-fd27-4dce-8be6-3d808040d8d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 298723c5031299b1b105f686e188e1e27cfd758c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965870"
---
# <a name="model-database"></a>model, base de données
  La base de données **model** fait office de modèle pour toutes les bases de données créées sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Étant donné que la base de données **tempdb** est créée chaque fois que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est démarré, la base de données **model** doit toujours exister sur un système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Tout le contenu de la base de données **model** , y compris ses options, est copié dans la nouvelle base de données. Certains paramètres de **model** sont également utilisés pour la création d'une nouvelle base de données **tempdb** au démarrage, de sorte que la base de données **model** doit toujours exister sur un système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Les bases de données utilisateur récemment créées utilisent le même [mode de récupération](../backup-restore/recovery-models-sql-server.md) que la base de données model. Le mode par défaut est configurable par l'utilisateur. Pour connaître le mode de récupération actuel du modèle, consultez [Afficher ou modifier le mode de récupération d’une base de données &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
> [!IMPORTANT]  
>  Si vous modifiez la base de données **model** avec des informations de modèle propres à l’utilisateur, nous vous recommandons de sauvegarder **model**. Pour plus d’informations, consultez [Sauvegarder et restaurer des bases de données système &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="model-usage"></a>Utilisation de la base de données model  
 Lorsqu'une instruction CREATE DATABASE est émise, le système crée la première partie de la base de données en copiant le contenu de la base de données **model** . Le reste de la nouvelle base de données est ensuite rempli de pages vides.  
  
 Si vous modifiez la base de données **model** , toutes les bases de données créées ultérieurement héritent des modifications apportées. Par exemple, vous pouvez définir des autorisations ou des options de base de données, ou bien ajouter des objets tels que des tables, des fonctions ou des procédures stockées. Les propriétés de fichier de la base de données **model** sont une exception et sont ignorées, à l'exception de la taille initiale du fichier de données.  
  
## <a name="physical-properties-of-model"></a>Propriétés physiques de la base de données model  
 Le tableau ci-dessous répertorie les valeurs de configuration initiales des fichiers journaux et de données **model** . Les tailles de ces fichiers peuvent varier légèrement en fonction des éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Fichier|Nom logique|Nom physique|Croissance du fichier|  
|----------|------------------|-------------------|-----------------|  
|Données primaires|modeldev|model.mdf|Croissance automatique de 10 % jusqu'à saturation du disque.|  
|Journal|modellog|modellog.ldf|Croissance automatique de 10 % jusqu'à un maximum de 2 téraoctets.|  
  
 Pour déplacer la base de données **model** ou les fichiers journaux, consultez [Déplacer des bases de données système](system-databases.md).  
  
### <a name="database-options"></a>Options de base de données  
 Le tableau ci-dessous indique la valeur par défaut de chaque option de la base de données **model** et précise si cette option est modifiable. Pour afficher les valeurs actuelles de ces options, utilisez l'affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Option de base de données|Valeur par défaut|Peut être modifiée|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Yes|  
|ANSI_NULL_DEFAULT|OFF|Yes|  
|ANSI_NULLS|OFF|Yes|  
|ANSI_PADDING|OFF|Yes|  
|ANSI_WARNINGS|OFF|Yes|  
|ARITHABORT|OFF|Yes|  
|AUTO_CLOSE|OFF|Yes|  
|AUTO_CREATE_STATISTICS|ACTIVÉ|Yes|  
|AUTO_SHRINK|OFF|Yes|  
|AUTO_UPDATE_STATISTICS|ACTIVÉ|Yes|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Yes|  
|CHANGE_TRACKING|OFF|No|  
|CONCAT_NULL_YIELDS_NULL|OFF|Yes|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Yes|  
|CURSOR_DEFAULT|GLOBAL|Yes|  
|Options de disponibilité de base de données|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Non<br /><br /> Yes<br /><br /> Oui|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Yes|  
|DB_CHAINING|OFF|No|  
|ENCRYPTION|OFF|Non|  
|NUMERIC_ROUNDABORT|OFF|Yes|  
|PAGE_VERIFY|CHECKSUM|Yes|  
|PARAMETERIZATION|SIMPLE|Oui|  
|QUOTED_IDENTIFIER|OFF|Yes|  
|READ_COMMITTED_SNAPSHOT|OFF|Yes|  
|RECOVERY|Dépend de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] édition<sup>1</sup>|Yes|  
|RECURSIVE_TRIGGERS|OFF|Oui|  
|Options de Service Broker|DISABLE_BROKER|No|  
|TRUSTWORTHY|OFF|No|  
  
 <sup>1</sup> pour vérifier le mode de récupération actuel de la base de données, consultez [afficher ou modifier le mode de récupération d’une base de données &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) ou [sys. databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).  
  
 Pour obtenir une description de ces options de base de données, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="restrictions"></a>Restrictions  
 Les opérations suivantes ne peuvent pas être effectuées sur la base de données **model** :  
  
-   ajout de groupes de fichiers ou de fichiers ;  
  
-   Modification du classement. Le classement par défaut est le classement du serveur.  
  
-   Modification du propriétaire de la base de données. La base de données**model** appartient à **sa**.  
  
-   Suppression de la base de données  
  
-   Suppression de l’utilisateur **invité** de la base de données.  
  
-   Activation de la capture des données modifiées.  
  
-   Participation à la mise en miroir de bases de données  
  
-   Suppression du groupe de fichiers primaire, du fichier de données primaire ou du fichier journal  
  
-   Changement du nom de la base de données ou du groupe de fichiers primaire  
  
-   Affectation de la valeur OFFLINE à la base de données.  
  
-   Affectation de la valeur READ_ONLY au groupe de fichiers primaire.  
  
-   Création de procédures, de vues ou de déclencheurs à l'aide de l'option WITH ENCRYPTION. La clé de chiffrement est liée à la base de données dans laquelle l'objet est créé. Les objets chiffrés créés dans la base de données **model** peuvent être utilisés uniquement dans **model**.  
  
## <a name="related-content"></a>Contenu associé  
 [Bases de données système](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Déplacer des fichiers de bases de données](move-database-files.md)  
  
  
