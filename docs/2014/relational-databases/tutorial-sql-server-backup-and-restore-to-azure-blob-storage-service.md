---
title: 'Didacticiel : Sauvegarde et restauration SQL Server dans le service Stockage Blob Azure | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b166930b5d077e7294fcdbc13449d40cab309425
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176114"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Didacticiel : Sauvegarde et restauration SQL Server dans le service Stockage Blob Azure
  Bienvenue dans le Prise en main avec SQL Server didacticiel sauvegarde et restauration avec le service de stockage d’objets BLOB Azure. Ce didacticiel vous aide à comprendre comment écrire des sauvegardes et les restaurer à partir du service Stockage Blob Azure.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel montre comment créer un compte de stockage Windows et un conteneur d'objets blob, créer des informations d'identification pour accéder au compte de stockage, écrire une sauvegarde dans le service d'objet blob et effectuer une restauration simple. Ce didacticiel est divisé en quatre leçons :  
  
 [Leçon 1 : Créer des objets de stockage Azure](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 Dans cette leçon, vous allez créer un compte de stockage Azure et un conteneur d’objets blob.  
  
 [Leçon 2 : Créer des informations d’identification SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 Dans cette leçon, vous allez créer des informations d’identification afin de stocker les informations de sécurité utilisées pour accéder au compte de stockage Azure.  
  
 [Leçon 3 : Écrire une sauvegarde de base de données complète dans le service Stockage Blob Azure](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 Dans cette leçon, vous allez publier une instruction T-SQL pour écrire une sauvegarde de la base de données AdventureWorks2012 dans le service Stockage Blob Azure.  
  
 [Leçon 4 : Effectuer une restauration d'une sauvegarde de base de données complète](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 Dans cette leçon, vous allez publier une instruction T-SQL pour effectuer une restauration d'une sauvegarde de la base de données que vous avez créée au cours de la leçon précédente.  
  
### <a name="requirements"></a>Spécifications  
 Pour suivre ce didacticiel, vous devez connaître les concepts de sauvegarde et de restauration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et la syntaxe T-SQL. Pour utiliser ce didacticiel, votre système doit répondre aux spécifications suivantes :  
  
-   Une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et la base de données AdventureWorks2012 doivent être installées.  
  
     L’instance SQL Server peut être installée sur site ou sur une machine virtuelle Azure.  
  
     Vous pouvez utiliser une base de données utilisateur en remplacement d'AdventureWorks2012, puis modifier la syntaxe TSQL en conséquence.  
  
-   Le compte d’utilisateur utilisé pour émettre les commandes BACKUP (sauvegarder) ou RESTORE (restaurer) doit figurer dans le rôle de base de données **db_backup operator** avec les autorisations **Modifier des informations d’identification** .  
  
### <a name="additional-reading"></a>Documentation supplémentaire  
 Les ressources suivantes sont des lectures recommandées afin de comprendre les concepts et les bonnes pratiques pour l’utilisation du service Stockage Blob Azure pour les sauvegardes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
1.  [Sauvegarde et restauration SQL Server avec le service Stockage Blob Azure](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Bonnes pratiques et résolution des problèmes liés à la sauvegarde SQL Server vers une URL](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
