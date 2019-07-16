---
title: 'Leçon 1 : Créer des objets de stockage Azure Windows | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 449f86b80b93055bb23fe4cd32ace10e15724dbc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210958"
---
# <a name="lesson-1-create-windows-azure-storage-objects"></a>Leçon 1 : Créer des objets de Stockage Microsoft Azure
  Avant de créer des sauvegardes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans le Cloud de stockage, vous devez tout d'abord créer un compte de stockage, puis un conteneur d'objets blob. La leçon 1 présente les étapes de connexion au portail de gestion Windows Azure, puis de création d'un compte de stockage et d'un conteneur d'objets blob.  
  
## <a name="create-a-storage-account"></a>Créer un compte de stockage  
 Pour créer un compte de stockage à partir du portail de gestion Windows Azure, procédez comme suit :  
  
1.  Connectez-vous au portail de gestion Windows Azure à l'aide de votre compte. Si vous n’avez pas un compte Windows Azure, [Profitez d’évaluation gratuite de 3 mois de Windows Azure](https://go.microsoft.com/fwlink/?LinkId=271927).  
  
     ![Écran de connexion Azure Windows](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "écran de connexion Azure Windows")  
  
2.  Utilisez les instructions étape par étape détaillées [ici](https://go.microsoft.com/fwlink/?LinkId=271926), pour créer un compte de stockage.  
  
3.  Accédez au compte de stockage créé à l'étape précédente. En bas au centre de la page web, cliquez sur **gérer les clés**. Les informations de compte sont affichées. Copiez le nom du compte de stockage et les clés d'accès. Ces informations sont nécessaires pour créer des informations d'identification stockées dans SQL. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise ces informations pour accéder au compte de stockage et créer des sauvegardes.  
  
     ![Capture d’écran de clés de compte de stockage Windows Azure](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "capture d’écran de clés de compte de stockage Windows Azure")  
  
    > [!NOTE]  
    >  Vous pouvez également créer un compte de stockage par programme à l'aide des API REST. Pour plus d’informations, consultez [créer un compte de stockage](https://go.microsoft.com/fwlink/?LinkId=271928).  
  
### <a name="create-a-blob-container"></a>Créer un conteneur d'objets blob  
 Un conteneur regroupe un ensemble d’objets blob. Tous les objets blob doivent figurer dans un conteneur. Un compte peut contenir un nombre illimité de conteneurs, mais doit comporter au moins un conteneur. Un conteneur peut stocker un nombre illimité d'objets blob.  
  
 Pour créer un conteneur, procédez comme suit :  
  
1.  Sélectionnez le compte de stockage, cliquez sur le **conteneurs** onglet et cliquez sur **ajouter un conteneur** en bas de l’écran qui s’ouvre une boîte de dialogue.  
  
     ![Création d’un conteneur dans le portail de gestion](../../2014/tutorials/media/backuptocloud.gif "création d’un conteneur dans le portail de gestion")  
  
2.  Entrez le nom du conteneur. Notez le nom de conteneur spécifié. Ces informations sont utilisées dans l'URL (chemin d'accès au fichier de sauvegarde) dans les instructions T-SQL des leçons 3 et 4.  
  
3.  Sélectionnez privé pour **Type d’accès**. Nous vous recommandons de créer des conteneurs privés pour sécuriser vos fichiers de sauvegarde.  
  
     ![Création d’un conteneur d’objets blob](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "création d’un conteneur d’objets blob")  
  
    > [!NOTE]  
    >  L'authentification auprès du compte de stockage est requise pour la sauvegarde et la restauration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] même si vous choisissez de créer un conteneur public.  
    >   
    >  Vous pouvez également créer un conteneur par programme à l'aide des API REST. Pour plus d’informations, consultez [créer un conteneur](https://go.microsoft.com/fwlink/?LinkId=271946).  
  
### <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Créer des informations d’identification SQL Server](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).  
  
  
