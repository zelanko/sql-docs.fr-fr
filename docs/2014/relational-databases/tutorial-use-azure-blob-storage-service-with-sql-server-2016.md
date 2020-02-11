---
title: 'Didacticiel : SQL Server de fichiers de données dans le service de stockage Azure | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a15f6735ef0ef79b7eb953445c926f60f6bfb12e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176088"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a>Tutoriel : Fichiers de données SQL Server dans le service Stockage Azure
  Bienvenue dans le didacticiel SQL Server fichiers de données dans le service de stockage Azure. Ce tutoriel explique comment stocker directement des fichiers de données SQL Server dans le service de stockage d’objets blob Azure.  
  
 La prise en charge de l’intégration de SQL Server pour le service de stockage d’objets BLOB Azure est SQL Server une amélioration de 2014. Pour obtenir une vue d’ensemble des fonctionnalités et des avantages de l’utilisation de cette fonctionnalité, consultez [SQL Server des fichiers de données dans Azure](databases/sql-server-data-files-in-microsoft-azure.md).  
  
## <a name="what-you-will-learn"></a>Contenu  
 Ce didacticiel vous montre comment stocker des fichiers de données SQL Server dans le service de stockage Azure en plusieurs leçons. Chaque leçon traite d' une tâche spécifique. Tout d’abord, vous allez apprendre à créer un compte de stockage et un conteneur dans Azure. Ensuite, vous allez apprendre à créer un SQL Server informations d’identification pour pouvoir intégrer SQL Server à Azure Storage. Ensuite, vous allez créer une base de données directement dans le stockage Azure. Par ailleurs, le didacticiel décrit le chiffrement, la migration et les scénarios de sauvegarde et de restauration.  
  
 Ce didacticiel est divisé en neuf leçons :  
  
 **[Leçon 1 : Créer un compte Stockage Azure et un conteneur](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 Dans cette leçon, vous allez créer un compte de stockage Azure et un conteneur.  
  
 **[Leçon 2. Créer une stratégie sur un conteneur et générer une signature d’accès partagé &#40;clé de&#41; SAS](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 Dans cette leçon, vous allez créer une stratégie sur le conteneur d'objets blob et générer une signature d'accès partagé.  
  
 **[Leçon 3 : Créer des informations d'identification SQL Server](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 Dans cette leçon, vous allez créer des informations d’identification afin de stocker les informations de sécurité utilisées pour accéder au compte de stockage Azure.  
  
 **[Leçons 4 : Créer une base de données dans Stockage Azure](../relational-databases/lesson-3-database-backup-to-url.md)**  
 Dans cette leçon, vous allez créer une base de données dans stockage Azure à l’aide de l’option créer un nom de fichier de base de données.  
  
 **[Leçon 5. &#40;facultatif&#41; chiffrer votre base de données à l’aide de TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 Dans cette leçon, vous allez chiffrer votre base de données à l'aide d'un chiffrement transparent des données (TDE) et d'un certificat de serveur.  
  
 **[Leçon 6 : Migrer une base de données d’une machine source locale vers une machine de destination dans Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 Dans cette leçon, vous migrez une base de données locale vers une machine virtuelle dans Azure à l’aide de l’option CREATe DATABASE FOR ATTACH.  
  
 **[Leçon 7 :Déplacer vos fichiers de données dans Stockage Azure](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 Dans cette leçon, vous allez déplacer vos fichiers de données vers le stockage Azure à l’aide de l’instruction ALTER DATABASE.  
  
 **[Leçon 8. Restaurer une base de données dans Azure Storage](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 Dans cette leçon, vous allez restaurer une base de données dans Azure Storage à l’aide de l’option RESTORE DATABASE MOVE.  
  
 **[Leçon 9. Restaurer une base de données à partir du stockage Azure](lesson-8-restore-as-new-database-from-log-backup.md)**  
 Dans cette leçon, vous allez restaurer une base de données à partir du stockage Azure à l’aide de l’option RESTORE DATABASE MOVE.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de données SQL Server dans Azure](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
