---
title: 'Leçon 1 : Créer des objets de stockage Azure | Microsoft Docs'
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
ms.openlocfilehash: 6c43678851427d6498e57e8a2297449825adfb4f
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154351"
---
# <a name="lesson-1-create-azure-storage-objects"></a>Leçon 1 : Créer des objets de stockage Azure
  Avant de créer des sauvegardes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans le Cloud de stockage, vous devez tout d'abord créer un compte de stockage, puis un conteneur d'objets blob. La leçon 1 vous guide tout au long des étapes de connexion à la Portail de gestion Azure, en créant un compte de stockage et un conteneur d’objets BLOB.  
  
## <a name="create-a-storage-account"></a>Créer un compte de stockage  
 Pour créer un compte de stockage à partir du Portail de gestion Azure, procédez comme suit:  
  
1.  Connectez-vous au Portail de gestion Azure à l’aide de votre compte. Si vous n’avez pas de compte Azure, [consultez la version d’évaluation gratuite de 3 mois d’Azure](https://go.microsoft.com/fwlink/?LinkId=271927).  
  
     ![Écran de connexion Azure](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Écran de connexion Azure")  
  
2.  Pour créer un compte de stockage, suivez les instructions pas à pas détaillées [ici](https://go.microsoft.com/fwlink/?LinkId=271926).  
  
3.  Accédez au compte de stockage créé à l'étape précédente. Dans le centre en bas de la page Web, cliquez sur **gérer les clés**. Les informations de compte sont affichées. Copiez le nom du compte de stockage et les clés d'accès. Ces informations sont nécessaires pour créer des informations d'identification stockées dans SQL. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise ces informations pour accéder au compte de stockage et créer des sauvegardes.  
  
     ![Capture d’écran des clés de compte de stockage Azure](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Capture d’écran des clés de compte de stockage Azure")  
  
    > [!NOTE]  
    >  Vous pouvez également créer un compte de stockage par programme à l'aide des API REST. Pour plus d’informations, consultez [créer un compte de stockage](https://go.microsoft.com/fwlink/?LinkId=271928).  
  
### <a name="create-a-blob-container"></a>Créer un conteneur d'objets blob  
 Un conteneur regroupe un ensemble d’objets blob. Tous les objets blob doivent figurer dans un conteneur. Un compte peut contenir un nombre illimité de conteneurs, mais doit comporter au moins un conteneur. Un conteneur peut stocker un nombre illimité d'objets blob.  
  
 Pour créer un conteneur, procédez comme suit :  
  
1.  Sélectionnez le compte de stockage, cliquez sur l’onglet **conteneurs** , puis cliquez sur **Ajouter un conteneur** en bas de l’écran pour ouvrir une nouvelle boîte de dialogue.  
  
     ![Création d’un conteneur dans le portail de gestion](../../2014/tutorials/media/backuptocloud.gif "Création d’un conteneur dans le portail de gestion")  
  
2.  Entrez le nom du conteneur. Notez le nom de conteneur spécifié. Ces informations sont utilisées dans l'URL (chemin d'accès au fichier de sauvegarde) dans les instructions T-SQL des leçons 3 et 4.  
  
3.  Sélectionnez privé pour le **type d’accès**. Nous vous recommandons de créer des conteneurs privés pour sécuriser vos fichiers de sauvegarde.  
  
     ![Création d’un conteneur d’objets BLOB](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "Création d’un conteneur d’objets BLOB")  
  
    > [!NOTE]  
    >  L'authentification auprès du compte de stockage est requise pour la sauvegarde et la restauration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] même si vous choisissez de créer un conteneur public.  
    >   
    >  Vous pouvez également créer un conteneur par programme à l'aide des API REST. Pour plus d’informations, consultez [créer un conteneur](https://go.microsoft.com/fwlink/?LinkId=271946).  
  
### <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Créez un SQL Server des](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)informations d’identification.  
  
  
