---
title: 'Leçon 2 : Créer des informations d’identification SQL Server | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b16012ed7ff12783e69add14cf8e51011668845e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152934"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Leçon 2 : Créer des informations d’identification SQL Server
  **Informations d'identification :** les informations d'identification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server.  Ici, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] processus de sauvegarde et restauration utilisent les informations d’identification pour s’authentifier auprès du service de stockage d’objets Blob Windows Azure. Les informations d'identification contiennent le nom du compte de stockage et ses valeurs de **clé d'accès** . Une fois les informations d'identification créées, vous devez les spécifier dans l'option WITH CREDENTIAL lorsque vous publiez des instructions BACKUP/RESTORE. Pour plus d'informations sur l'affichage, la copie ou la régénération des **access keys**de compte de stockage, consultez [Afficher, copier et régénérer les clés d'accès d'un compte de stockage Windows Azure](http://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Pour plus d'informations sur les informations d'identification en général, consultez [Informations d'identification](http://msdn.microsoft.com/library/ms161950.aspx).  
  
 Pour obtenir plus d'informations et d'autres exemples d'utilisation des informations d'identification, consultez [Créer un proxy de SQL Server Agent](http://msdn.microsoft.com/library/ms175834.aspx).  
  
> [!IMPORTANT]  
>  La configuration requise pour la création des informations d’identification SQL Server décrites ci-dessous est spécifique au processus de sauvegarde de SQL Server ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), et [sauvegarde managée SQL Server vers Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server, lorsqu'il accède au stockage Azure pour écrire ou lire des sauvegardes, utilise le nom du compte de stockage et les informations de clé d'accès.  Pour plus d’informations sur la création des informations d’identification pour stocker les fichiers de base de données dans le stockage Azure, consultez [leçon 3 : créer des informations d’identification SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Créer des informations d'identification SQL Server  
 Pour créer des informations d'identification SQL Server, procédez comme suit :  
  
1.  Connectez-vous à SQL Server Management Studio.  
  
2.  Dans l'Explorateur d'objets, connectez-vous à l'instance du moteur de base de données sur lequel la base de données AdventureWorks2012 est installée, ou utilisez la base de données que vous envisagez d'utiliser pour ce didacticiel.  
  
3.  Dans la barre d'outils **standard** , cliquez sur **Nouvelle requête**.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![mappage de compte de stockage pour les informations d’identification sql](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "mappage de compte de stockage pour les informations d’identification sql")  
  
5.  Vérifiez l'instruction T-SQL et cliquez sur **Exécuter**.  
  
 Pour plus d’informations sur le service de stockage d’objets Blob Windows Azure pour les concepts de sauvegarde et de la configuration requise, consultez [SQL Server Backup and Restore with Windows Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Leçon suivante  
 [Leçon 3 : Écrire une sauvegarde complète de la base de données dans le Service de stockage Windows Azure Blob](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).  
  
  