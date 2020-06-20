---
title: 'Leçon 1 : créer un compte et un conteneur de stockage Azure | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4c0f364b15053e589d87b715d124bae48a87461e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039868"
---
# <a name="lesson-1-create-azure-storage-account-and-container"></a>Leçon 1 : Créer un compte et un conteneur Stockage Azure
  Avant de pouvoir commencer à stocker des SQL Server fichiers de données dans le stockage Azure, vous devez d’abord créer un compte de stockage Azure et un conteneur d’objets BLOB, ainsi qu’une signature d’accès partagé. La leçon 1 vous guide tout au long des étapes de connexion à Azure Portail de gestion, de création d’un compte de stockage, d’un conteneur d’objets BLOB et d’une signature d’accès partagé.  
  
 Par défaut, seul le propriétaire du compte de stockage peut accéder aux objets blob, aux tables et aux files d’attente dans ce compte. Pour accéder à ces ressources en utilisant cette nouvelle amélioration SQL Server sans partager la clé d'accès du compte de stockage, effectuez les tâches suivantes :  
  
-   Définissez les autorisations du conteneur avec un accès privé.  
  
-   Créez une signature d'accès partagé. Elle vous permet de déléguer l'accès restreint à un conteneur, à un objet blob, à une table ou à une ressource de file d'attente en spécifiant l'intervalle pendant lequel les ressources sont disponibles et les autorisations dont disposera un client.  
  
-   Utilisez une stratégie d'accès stockée pour gérer les signatures d'accès partagé d'un conteneur ou de ses objets blob. La stratégie d'accès stockée vous donne une mesure supplémentaire de contrôle de vos signatures d'accès partagé et fournit également un moyen simple de les révoquer.  
  
 Pour plus d’informations, consultez [gérer l’accès aux ressources de stockage Azure](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).  
  
## <a name="create-storage-account"></a>Créer un compte de stockage  
 Pour créer un compte de stockage sur le Portail de gestion Azure, procédez comme suit :  
  
1.  Connectez-vous au [portail de gestion Azure](https://manage.windowsazure.com) à l’aide de votre compte. Si vous n'avez pas de compte Azure, visitez la page [Version d'évaluation gratuite d'Azure](https://www.windowsazure.com/pricing/free-trial/).  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  Suivez les instructions détaillées pour [créer un compte de stockage](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/). Notez que lorsque vous créez un compte de stockage à utiliser pour la fonctionnalité fichiers de données SQL Server dans Azure, vous devez désélectionner ou désactiver la géo-réplication. Cela est dû au fait que l'ordre d'écriture n'est pas garanti pour plusieurs objets blob participant à la géoréplication. Si un compte de stockage est géorépliqué et la récupération est requise, une altération se produit.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Créer un conteneur d’objets blob  
 Dans Azure, un conteneur permet de regrouper un ensemble d’objets BLOB. Tous les objets blob doivent figurer dans un conteneur. Un compte de stockage peut contenir un nombre illimité de conteneurs, mais doit comporter au moins un conteneur. Un conteneur peut stocker un nombre illimité d’objets blob. Pour obtenir les informations les plus récentes sur les limites de taille de stockage, consultez la page [utilisation du service de stockage d’objets BLOB Azure dans .net](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Pour créer un conteneur dans Azure, procédez comme suit :  
  
1.  Connectez-vous au [Portail de gestion Azure](https://manage.windowsazure.com).  
  
2.  Sélectionnez le compte de stockage, cliquez sur l'onglet **Conteneurs** , puis cliquez sur **Ajouter un conteneur** en bas de l'écran pour ouvrir une nouvelle boîte de dialogue.  
  
3.  Entrez le nom du conteneur.  
  
4.  Sélectionnez **Privé** pour le **Type d'accès**. Lorsque vous définissez l’accès privé, le conteneur et les données BLOB ne peuvent être lus que par le propriétaire du compte Azure.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  Pour créer un conteneur par programme, utilisez également des API REST. Pour plus d’informations, consultez [créer un conteneur](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) et également référence de l' [API REST des services de stockage Azure](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).  
  
 **Leçon suivante :**  
  
 [Leçon 2. Créer une stratégie sur un conteneur et générer une signature d’accès partagé &#40;clé de&#41; SAS](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
