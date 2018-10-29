---
title: 'Didacticiel : Sauvegarde et restauration SQL Server dans le service Stockage Blob Azure | Microsoft Docs'
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a33c2bd47bae8bede7fa71e1654627c123e7cdbc
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874317"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Didacticiel : Sauvegarde et restauration SQL Server dans le service Stockage Blob Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Ce tutoriel vous aide à comprendre comment écrire des sauvegardes et les restaurer à partir du service Stockage Blob Azure.  Ce tutoriel explique comment créer un conteneur d’objets blob Azure et des informations d’identification pour accéder au compte de stockage, écrire une sauvegarde dans le service d’objets blob et effectuer une restauration simple.
  
### <a name="prerequisites"></a>Conditions préalables requises  
Pour suivre ce didacticiel, vous devez connaître les concepts de sauvegarde et de restauration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et la syntaxe T-SQL. Pour utiliser ce tutoriel, vous avez besoin d’un compte de stockage Azure, de SQL Server Management Studio (SSMS), d’un accès à un serveur qui exécute SQL Server et d’une base de données AdventureWorks. Par ailleurs, le compte utilisé pour émettre les commandes BACKUP et RESTORE doit figurer dans le rôle de base de données **db_backupoperator** avec les autorisations **modifier les informations d’identification**. 

- Obtenir gratuitement un [compte Azure](https://azure.microsoft.com/offers/ms-azr-0044p/).
- Créer un [compte de stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=portal).
- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Téléchargez les [exemples de bases de données AdventureWorks2016](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).
- Affectez le compte utilisateur au rôle de [db_backupoperator](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles) et autorisez [modifier les informations d’identification](https://docs.microsoft.com/sql/t-sql/statements/alter-credential-transact-sql). 


## <a name="create-azure-blob-container"></a>Créer un conteneur d’objets blob Azure
Un conteneur regroupe un ensemble d’objets blob. Tous les objets blob doivent figurer dans un conteneur. Un compte peut contenir un nombre illimité de conteneurs, mais doit comporter au moins un conteneur. Un conteneur peut stocker un nombre illimité d'objets blob. 

Pour créer un conteneur, suivez ces étapes :

1. Ouvrez le portail Azure. 
1. Accédez à votre compte de stockage. 
   1. Sélectionnez le compte de stockage et faites défiler l’affichage jusqu'à **Services d’objets Blob**.
   1. Sélectionnez **Objets blob**, puis sélectionnez +**Conteneur** pour ajouter un nouveau conteneur. 
   1. Entrez le nom du conteneur et notez le nom de conteneur que vous avez spécifié. Ces informations sont utilisées dans l'URL (chemin d'accès au fichier de sauvegarde) dans les instructions T-SQL, plus loin dans ce tutoriel. 
   1. Sélectionnez **OK**. 
    
    ![Nouveau conteneur](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/new-container.png)


  >[!NOTE]
  >L'authentification auprès du compte de stockage est requise pour la sauvegarde et la restauration SQL Server même si vous choisissez de créer un conteneur public. Vous pouvez également créer un conteneur par programmation à l'aide des API REST. Pour plus d'informations, consultez [Créer un conteneur](https://docs.microsoft.com/rest/api/storageservices/Create-Container).


## <a name="create-a-sql-server-credential"></a>Créer des informations d'identification SQL Server
Les informations d'identification SQL Server sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server. Ici, les processus de sauvegarde et de restauration SQL Server utilisent des informations d'identification pour s’authentifier auprès du service de stockage d'objets Blob de Microsoft Azure. Les informations d'identification contiennent le nom du compte de stockage et ses valeurs de **clé d'accès** . Une fois les informations d'identification créées, vous devez les spécifier dans l'option WITH CREDENTIAL lorsque vous publiez des instructions BACKUP/RESTORE. Pour plus d’informations sur les informations d’identification, consultez [Informations d’identification](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/credentials-database-engine). 

  >[!IMPORTANT]
  >La configuration requise pour créer des informations d'identification SQL Server décrite ci-dessous est spécifique aux processus de sauvegarde SQL Server ([Sauvegarde SQL Server vers une URL](backup-restore/sql-server-backup-to-url.md) et [Sauvegarde managée SQL Server sur Microsoft Azure](backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server, lorsqu'il accède au stockage Azure pour écrire ou lire des sauvegardes, utilise le nom du compte de stockage et les informations de clé d'accès.

### <a name="access-keys"></a>Clés d'accès
Étant donné que le portail Azure est encore ouvert, enregistrez les clés d’accès nécessaires pour créer les informations d’identification. 

1. Accédez au **compte de stockage** dans le portail Azure. 
1. Faites défiler l’affichage jusqu'à **Paramètres** et sélectionnez **Clés d’accès**. 
1. Enregistrez la clé et la chaîne de connexion à utiliser ultérieurement dans ce tutoriel. 

   ![Clés d'accès](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/access-keys.png)

### <a name="create-a-sql-server-credential"></a>Créer des informations d'identification SQL Server
À l’aide de la clé d’accès que vous avez enregistrée, créez les informations d’identification SQL Server en suivant la procédure ci-dessous. 

1. Connectez-vous à votre serveur SQL Server en utilisant SQL Server Management Studio. 
1. Sélectionnez la base de données **AdventureWorks2016** et ouvrez une fenêtre **Nouvelle requête**. 
1. Copiez, collez et exécutez l'exemple suivant dans la fenêtre de requête, et modifiez-le si nécessaire : 

  ```sql
  CREATE CREDENTIAL mycredential   
  WITH IDENTITY= 'msftutorialstorage', -- this is the name of the storage account you specified when creating a storage account   
  SECRET = '<storage account access key>' -- this should be either the Primary or Secondary Access Key for the storage account 
  ```
1. Exécutez cette instruction pour créer les informations d’identification. 

## <a name="backup-database-to-the-windows-azure-blob-storage-service"></a>Sauvegarder la base de données dans le service Stockage Blob Microsoft Azure
Dans cette section, vous allez utiliser une instruction T-SQL pour effectuer une sauvegarde de base de données complète dans le service Stockage Blob Microsoft Azure. 

1. Connectez-vous à votre serveur SQL Server en utilisant SQL Server Management Studio. 
1. Sélectionnez la base de données **AdventureWorks2016** et ouvrez une fenêtre **Nouvelle requête**. 
1. Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire : 

 ```sql
 BACKUP DATABASE [AdventureWorks2016] 
 TO URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/ 
 WITH CREDENTIAL = 'mycredential';
 /* name of the credential you created in the previous step */ 
 GO
 ```
1. Exécutez l’instruction pour sauvegarder votre base de données AdventureWorks2016 vers une URL. 

 
## <a name="restore-database-from-windows-azure-blob-storage-service"></a>Restaurer la base de données à partir du service Stockage Blob Microsoft Azure
Dans cette section, vous allez utiliser une instruction T-SQL pour restaurer la sauvegarde de base de données complète. 

1. Connectez-vous à votre serveur SQL Server en utilisant SQL Server Management Studio. 
1. Ouvrez une fenêtre **Nouvelle requête**. 
1. Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire : 

 ```sql
 RESTORE DATABASE AdventureWorks2016 
 FROM URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 WITH CREDENTIAL = 'mycredential',
 STATS = 5 -- use this to see monitor the progress
 GO
 ``` 

## <a name="see-also"></a>Voir aussi 
Les ressources suivantes sont des lectures recommandées afin de mieux comprendre les concepts et les bonnes pratiques pour l’utilisation du service Stockage Blob Azure pour les sauvegardes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   [Sauvegarde et restauration SQL Server avec le service de stockage d’objets blob Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
-   [Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
