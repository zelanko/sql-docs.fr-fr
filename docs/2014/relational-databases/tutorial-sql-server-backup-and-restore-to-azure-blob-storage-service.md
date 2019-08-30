---
title: 'Tutoriel : Sauvegarde et restauration SQL Server avec le service Stockage Blob Azure | Microsoft Docs'
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
ms.openlocfilehash: 8a9cbb46b04491be3fe97cb707ad79c98990ff19
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155328"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Tutoriel : Sauvegarde et restauration SQL Server avec le service Stockage Blob Azure
  Bienvenue dans le Prise en main avec SQL Server didacticiel sauvegarde et restauration avec le service de stockage d’objets BLOB Azure. Ce didacticiel vous aide à comprendre comment écrire des sauvegardes et les restaurer à partir du service Stockage Blob Azure.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel montre comment créer un compte de stockage Windows et un conteneur d'objets blob, créer des informations d'identification pour accéder au compte de stockage, écrire une sauvegarde dans le service d'objet blob et effectuer une restauration simple. Ce didacticiel est divisé en quatre leçons :  
  
 [Leçon 1 : Créer des objets de stockage Azure](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 Dans cette leçon, vous allez créer un compte de stockage Azure et un conteneur d’objets BLOB.  
  
 [Leçon 2 : Créer des informations d’identification de SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 Dans cette leçon, vous allez créer des informations d’identification afin de stocker les informations de sécurité utilisées pour accéder au compte de stockage Azure.  
  
 [Leçon 3 : Écrire une sauvegarde de base de données complète dans le service de stockage d’objets BLOB Azure](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 Dans cette leçon, vous allez publier une instruction T-SQL pour écrire une sauvegarde de la base de données AdventureWorks2012 dans le service Stockage Blob Azure.  
  
 [Leçon 4 : Effectuer une restauration à partir d’une sauvegarde complète de base de données](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 Dans cette leçon, vous allez publier une instruction T-SQL pour effectuer une restauration d'une sauvegarde de la base de données que vous avez créée au cours de la leçon précédente.  
  
### <a name="requirements"></a>Configuration requise  
 Pour suivre ce didacticiel, vous devez connaître les concepts de sauvegarde et de restauration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et la syntaxe T-SQL. Pour utiliser ce didacticiel, votre système doit répondre aux spécifications suivantes :  
  
-   Une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et la base de données AdventureWorks2012 doivent être installées.  
  
     L’instance de SQL Server peut être locale ou dans une machine virtuelle Azure.  
  
     Vous pouvez utiliser une base de données utilisateur en remplacement d'AdventureWorks2012, puis modifier la syntaxe TSQL en conséquence.  
  
-   Le compte d’utilisateur utilisé pour émettre les commandes BACKUP (sauvegarder) ou RESTORE (restaurer) doit figurer dans le rôle de base de données **db_backup operator** avec les autorisations **Modifier des informations d’identification** .  
  
### <a name="additional-reading"></a>Lecture supplémentaire  
 Les ressources suivantes sont des lectures recommandées afin de comprendre les concepts et les bonnes pratiques pour l’utilisation du service Stockage Blob Azure pour les sauvegardes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
1.  [SQL Server la sauvegarde et la restauration avec le service de stockage d’objets BLOB Azure](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Bonnes pratiques en matière de sauvegarde SQL Server vers une URL et résolution des problèmes associés](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
