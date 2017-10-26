---
title: "Leçon 2 : Créer des informations d’identification SQL Server à l’aide d’une signature d’accès partagé | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/25/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f6e88b211fc2a053ffeadb038298a28179a94d88
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-create-a-sql-server-credential-using-a-shared-access-signature"></a>Leçon 2 : Créer des informations d’identification SQL Server à l’aide d’une signature d’accès partagé
Dans cette leçon, vous allez créer des informations d’identification pour stocker les informations de sécurité dont se servira SQL Server pour écrire et lire dans le conteneur Azure que vous avez créé à la [Leçon 1 : Créer une stratégie d’accès stockée et une signature d’accès partagé sur un conteneur Azure](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md).  
  
Les informations d'identification SQL Server sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server. Les informations d’identification contiennent le chemin de l’URI du conteneur de stockage et la signature d’accès partagé pour ce conteneur.  
  
> [!NOTE]  
> Si vous souhaitez effectuer une sauvegarde d’une base de données SQL Server 2012 SP1 CU2 ou version ultérieure ou d’une base de données SQL Server 2014 vers ce conteneur Azure, vous pouvez utiliser la [syntaxe déconseillée](https://technet.microsoft.com/en-US/library/dn435916(v=sql.120).aspx) décrite ici pour créer des informations d’identification SQL Server en fonction de votre clé de compte de stockage.  
  
## <a name="create-sql-server-credential"></a>Créer des informations d’identification SQL Server  
Pour créer des informations d’identification SQL Server, procédez comme suit :  
  
1.  Connectez-vous à SQL Server Management Studio.  
  
2.  Ouvrez une nouvelle fenêtre de requête et connectez-vous à l’instance SQL Server 2016 du moteur de base de données dans votre environnement local.  
  
3.  Dans la nouvelle fenêtre de requête, collez l’instruction CREATE CREDENTIAL avec la signature d’accès partagé issue de la leçon 1, puis exécutez ce script.  
  
    Le script ressemble au code suivant.  
  
    ```Transact-SQL  
  
    USE master  
    CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] – this name must match the container path, start with https and must not contain a forward slash.  
       WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
       , SECRET = 'sharedaccesssignature' –- this is the shared access signature key that you obtained in Lesson 1.   
    GO  
  
    ```  
  
4.  Pour voir toutes les informations d’identification disponibles, exécutez l’instruction suivante dans une fenêtre de requête connectée à votre instance :  
  
    ```Transact-SQL  
    SELECT * from sys.credentials  
    ```  
  
5.  Ouvrez une nouvelle fenêtre de requête et connectez-vous à l’instance SQL Server 2016 du moteur de base de données dans votre machine virtuelle Azure.  
  
6.  Dans la nouvelle fenêtre de requête, collez l’instruction CREATE CREDENTIAL avec la signature d’accès partagé issue de la leçon 1, puis exécutez ce script.  
  
7.  Répétez les étapes 5 et 6 pour toute instance SQL Server 2016 supplémentaire devant avoir accès au conteneur Azure.  
  
**Leçon suivante :**  
  
[Leçon 3 : Sauvegarder une base de données vers une URL](../relational-databases/lesson-3-database-backup-to-url.md)  
  
## <a name="see-also"></a>Voir aussi  
[Informations d’identification &#40;moteur de base de données&#41;](../relational-databases/security/authentication-access/credentials-database-engine.md)  
[CREATE CREDENTIAL &#40;Transact-SQL&#41;](../t-sql/statements/create-credential-transact-sql.md)  
[sys.credentials &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  


