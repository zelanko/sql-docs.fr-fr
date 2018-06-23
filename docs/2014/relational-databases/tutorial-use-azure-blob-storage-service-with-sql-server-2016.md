---
title: 'Didacticiel : Fichiers de données du serveur SQL dans le service de stockage Windows Azure | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd793aad219d8e65a787dd3d872046df00cca414
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153207"
---
# <a name="tutorial-sql-server-data-files-in-windows-azure-storage-service"></a>Didacticiel : fichiers de données SQL Server dans le service de Stockage Microsoft Azure
  Bienvenue dans le didacticiel Fichiers de données SQL Server dans le service de Stockage Microsoft Azure. Ce didacticiel explique comment stocker directement des fichiers de données SQL Server dans le service de stockage d'objets blob Windows Azure.  
  
 La prise en charge de l'intégration de SQL Server au service de stockage d'objets blob Windows Azure est une amélioration de SQL Server 2014. Pour une vue d’ensemble des fonctionnalités et avantages de l’utilisation de cette fonctionnalité, consultez [fichiers de données SQL Server dans Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md).  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel vous montre comment stocker des fichiers de données SQL Server dans le service de Stockage Microsoft Azure en plusieurs leçons. Chaque leçon traite d' une tâche spécifique. Tout d'abord, vous apprendrez à créer un compte de stockage et un conteneur dans Windows Azure. Ensuite, vous découvrirez comment créer des informations d'identification SQL Server pour pouvoir intégrer SQL Server au Stockage Microsoft Azure. Puis, vous allez créer une base de données directement dans le Stockage Microsoft Azure. Par ailleurs, le didacticiel décrit le chiffrement, la migration et les scénarios de sauvegarde et de restauration.  
  
 Ce didacticiel est divisé en neuf leçons :  
  
 **[Leçon 1 : Créer le compte de stockage Azure de Windows et un conteneur](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 Dans cette leçon, vous allez créer un compte de Stockage Microsoft Azure et un conteneur.  
  
 **[Leçon 2. Créer une stratégie sur le conteneur et générer une Signature d’accès partagé &#40;SAS&#41; clé](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 Dans cette leçon, vous allez créer une stratégie sur le conteneur d'objets blob et générer une signature d'accès partagé.  
  
 **[Leçon 3 : Créer des informations d’identification SQL Server](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 Dans cette leçon, vous allez créer des informations d'identification afin de stocker les informations de sécurité utilisées pour accéder au compte de stockage Windows Azure.  
  
 **[Leçon 4 : Créer une base de données dans le stockage Windows Azure](../relational-databases/lesson-3-database-backup-to-url.md)**  
 Dans cette leçon, vous allez créer une base de données dans le Stockage Microsoft Azure à l'aide de l'option CREATE Database FILENAME.  
  
 **[Leçon 5. &#40;Facultatif&#41; chiffrer votre base de données à l’aide du chiffrement transparent des données](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 Dans cette leçon, vous allez chiffrer votre base de données à l'aide d'un chiffrement transparent des données (TDE) et d'un certificat de serveur.  
  
 **[Leçon 6 : Migrer une base de données à partir d’une source de l’ordinateur local vers un ordinateur de destination dans Windows Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 Dans cette leçon, vous allez migrer une base de données d'un emplacement local vers un ordinateur virtuel dans Windows Azure à l'aide de l'option CREATE DATABASE FOR ATTACH.  
  
 **[Leçon 7 : Déplacer vos fichiers de données vers le stockage Windows Azure](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 Dans cette leçon, vous allez déplacer les fichiers de données vers le Stockage Microsoft Azure à l'aide de l'instruction ALTER DATABASE.  
  
 **[Leçon 8. Restaurer une base de données pour le stockage Windows Azure](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 Dans cette leçon, vous allez restaurer une base de données dans le Stockage Microsoft Azure à l'aide de l'option RESTORE Database MOVE.  
  
 **[Leçon 9. Restaurer une base de données du stockage Windows Azure](lesson-8-restore-as-new-database-from-log-backup.md)**  
 Dans cette leçon, vous allez restaurer une base de données depuis le Stockage Microsoft Azure à l'aide de l'option RESTORE Database MOVE.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de données SQL Server dans Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  