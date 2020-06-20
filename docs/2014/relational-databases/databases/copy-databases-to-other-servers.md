---
title: Copier des bases de données sur d’autres serveurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bcde6185f25129596b4be7a150d4ee230c54c1a0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84952088"
---
# <a name="copy-databases-to-other-servers"></a>Copier des bases de données sur d'autres serveurs
  Il est parfois utile de copier une base de données d'un ordinateur vers un autre, notamment pour des tests, la vérification de cohérence, le développement de logiciels, l'exécution de rapports, la création d'une base de données miroir ou éventuellement pour rendre la base de données disponible pour des opérations à distance.  
  
 Il existe plusieurs méthodes pour copier une base de données :  
  
-   Utilisation de l'Assistant Copie de base de données  
  
     Vous pouvez utiliser l'Assistant Copie de base de données pour copier ou déplacer des bases de données entre des serveurs ou pour mettre à niveau une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une version ultérieure. Pour plus d'informations, consultez [Use the Copy Database Wizard](use-the-copy-database-wizard.md).  
  
-   Restauration d'une sauvegarde de base de données  
  
     Pour copier la totalité d'une base de données, vous pouvez utiliser les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] BACKUP et RESTORE. La restauration d'une sauvegarde complète d'une base de données est généralement utilisée pour copier la base de données d'un ordinateur à un autre pour diverses raisons. Pour plus d’informations sur l’utilisation des opérations de sauvegarde et de restauration pour copier une base de données, consultez [Copier des bases de données avec la sauvegarde et la restauration](copy-databases-with-backup-and-restore.md).  
  
    > [!NOTE]  
    >  Pour configurer une base de données miroir en vue d’une mise en miroir, restaurez la base de données sur le serveur miroir à l’aide de RESTORE DATABASE *<nom_base_de_données>* WITH NORECOVERY. Pour plus d’informations, consultez [Préparer une base de données miroir pour la mise en miroir &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Utilisation de l'Assistant Génération de scripts pour publier des bases de données  
  
     Vous pouvez utiliser l'Assistant Génération de scripts pour transférer une base de données d'un ordinateur local à un fournisseur d'hébergement Web. Pour plus d’informations, consultez [Assistant Générer et publier des scripts](../scripting/generate-and-publish-scripts-wizard.md).  
  
  
