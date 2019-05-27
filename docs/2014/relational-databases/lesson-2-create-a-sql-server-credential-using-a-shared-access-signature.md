---
title: 'Leçon 3 : Créer des informations d’identification SQL Server | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85e60c359df2a209742b5b10693fcb72ac9cb37a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66090851"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Leçon 3 : Créer des informations d'identification SQL Server
  Dans cette leçon, vous allez créer des informations d'identification afin de stocker les informations de sécurité utilisées pour accéder au compte de stockage Windows Azure.  
  
 Les informations d'identification SQL Server sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server. Les informations d'identification contiennent le chemin d'accès de l'URI du conteneur de stockage et les valeurs de clé de signature d'accès partagé. Pour chaque conteneur de stockage utilisé par un fichier de données ou un fichier journal, vous devez créer des informations d'identification SQL Server dont le nom correspond au chemin d'accès du conteneur.  
  
 Pour obtenir des informations générales sur les informations d’identification, consultez [informations d’identification &#40;moteur de base de données&#41;](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  La configuration requise pour la création d’une information d’identification SQL Server décrite ci-dessous est spécifique à la [fichiers de données SQL Server dans Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md) fonctionnalité. Pour plus d’informations sur la création des informations d’identification pour le processus de sauvegarde dans le stockage Azure, consultez [leçon 2 : Créer des informations d’identification SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md).  
  
 Pour créer des informations d'identification SQL Server, procédez comme suit :  
  
1.  Connectez-vous à SQL Server Management Studio.  
  
2.  Dans l'Explorateur d'objets, connectez-vous à l'instance du moteur de base de données installée.  
  
3.  Dans la barre d'outils standard, cliquez sur Nouvelle requête.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire. L’instruction suivante crée une information d’identification du serveur SQL pour stocker le certificat d’accès partagé de votre conteneur de stockage.  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     Pour plus d’informations, consultez [CREATE CREDENTIAL &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-credential-transact-sql) dans la documentation en ligne de SQL Server.  
  
5.  Pour voir toutes les informations d'identification disponibles, exécutez l'instruction suivante dans la fenêtre de requête :  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Pour plus d’informations sur sys.credentials, consultez [sys.credentials &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) dans la documentation en ligne de SQL Server.  
  
 **Leçon suivante :**  
  
 [Leçon 4 : Créer une base de données dans le stockage Windows Azure](lesson-3-database-backup-to-url.md)  
  
  
