---
title: 'Leçon 2 : Créer des informations d’identification de SQL Server | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: baa337d33173f292145d92b60d6192af2a716c5e
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "70154330"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Leçon 2 : Créer des informations d'identification SQL Server
  **Informations d’identification :** Les informations d'identification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server.  Ici, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] les processus de sauvegarde et de restauration utilisent les informations d’identification pour s’authentifier auprès du service de stockage d’objets BLOB Azure. Les informations d'identification contiennent le nom du compte de stockage et ses valeurs de **clé d'accès** . Une fois les informations d'identification créées, vous devez les spécifier dans l'option WITH CREDENTIAL lorsque vous publiez des instructions BACKUP/RESTORE. Pour plus d'informations sur l'affichage, la copie ou la régénération des **access keys**de compte de stockage, consultez [Afficher, copier et régénérer les clés d'accès d'un compte de stockage Windows Azure](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Pour plus d'informations sur les informations d'identification en général, consultez [Informations d'identification](../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Pour obtenir plus d'informations et d'autres exemples d'utilisation des informations d'identification, consultez [Créer un proxy de SQL Server Agent](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  La configuration requise pour la création d’une SQL Server informations d’identification décrites ci-dessous est spécifique aux processus de sauvegarde SQL Server ([SQL Server sauvegarde vers une URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)et [SQL Server la sauvegarde managée dans Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server, lorsqu'il accède au stockage Azure pour écrire ou lire des sauvegardes, utilise le nom du compte de stockage et les informations de clé d'accès.  Pour plus d’informations sur la création d’informations d’identification pour le stockage des fichiers [de base de données dans Azure Storage, consultez la leçon 3 : Créer des informations d’identification de SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Créer des informations d'identification SQL Server  
 Pour créer des informations d'identification SQL Server, procédez comme suit :  
  
1.  Connectez-vous à SQL Server Management Studio.  
  
2.  Dans l'Explorateur d'objets, connectez-vous à l'instance du moteur de base de données sur lequel la base de données AdventureWorks2012 est installée, ou utilisez la base de données que vous envisagez d'utiliser pour ce didacticiel.  
  
3.  Dans la barre d'outils **standard** , cliquez sur **Nouvelle requête**.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![mappage du compte de stockage aux informations d’identification SQL] (../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "mappage du compte de stockage aux informations d’identification SQL")  
  
5.  Vérifiez l'instruction T-SQL et cliquez sur **Exécuter**.  
  
 Pour plus d’informations sur le service de stockage d’objets BLOB Azure pour les concepts et la configuration requise pour la sauvegarde, consultez [SQL Server la sauvegarde et la restauration avec le service de stockage d’objets BLOB Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Leçon suivante  
 [Leçon 3 : Écrire une sauvegarde de base de données complète dans le service](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)de stockage d’objets BLOB Azure.  
  
  
