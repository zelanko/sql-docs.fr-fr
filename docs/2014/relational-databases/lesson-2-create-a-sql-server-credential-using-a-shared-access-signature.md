---
title: 'Leçon 3 : Créer des informations d’identification SQL Server | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 201863a1df64cdc85ef41a55170948dbf4eba419
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151894"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Leçon 3 : Créer des informations d'identification SQL Server
  Dans cette leçon, vous allez créer des informations d'identification afin de stocker les informations de sécurité utilisées pour accéder au compte de stockage Windows Azure.  
  
 Les informations d'identification SQL Server sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server. Les informations d'identification contiennent le chemin d'accès de l'URI du conteneur de stockage et les valeurs de clé de signature d'accès partagé. Pour chaque conteneur de stockage utilisé par un fichier de données ou un fichier journal, vous devez créer des informations d'identification SQL Server dont le nom correspond au chemin d'accès du conteneur.  
  
 Pour obtenir des informations générales sur les informations d’identification, consultez [informations d’identification &#40;moteur de base de données&#41;](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  La configuration requise pour la création des informations d’identification SQL Server décrites ci-dessous est spécifique à la [fichiers de données SQL Server dans Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md) fonctionnalité. Pour plus d’informations sur la création des informations d’identification pour le processus de sauvegarde dans le stockage Azure, consultez [leçon 2 : créer des informations d’identification SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md).  
  
 Pour créer des informations d'identification SQL Server, procédez comme suit :  
  
1.  Connectez-vous à SQL Server Management Studio.  
  
2.  Dans l'Explorateur d'objets, connectez-vous à l'instance du moteur de base de données installée.  
  
3.  Dans la barre d'outils standard, cliquez sur Nouvelle requête.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire. L'instruction suivante va créer des informations d'identification SQL Server pour enregistrer votre certificat d'accès partagé du conteneur de stockage.  
  
    ```tsql  
  
    USE master  
    CREATE CREDENTIAL credentialname – this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' –- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     Pour plus d’informations, consultez [CREATE CREDENTIAL &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-credential-transact-sql) dans la documentation en ligne de SQL Server.  
  
5.  Pour voir toutes les informations d'identification disponibles, exécutez l'instruction suivante dans la fenêtre de requête :  
  
    ```tsql  
    SELECT * from sys.credentials  
    ```  
  
     Pour plus d’informations sur sys.credentials, consultez [sys.credentials &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) dans la documentation en ligne de SQL Server.  
  
 **Leçon suivante :**  
  
 [Leçon 4 : Créer une base de données dans le stockage Windows Azure](lesson-3-database-backup-to-url.md)  
  
  
