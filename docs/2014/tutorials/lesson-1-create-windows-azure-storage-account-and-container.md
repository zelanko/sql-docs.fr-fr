---
title: 'Leçon 1 : Créer le compte de stockage Azure Windows et conteneur | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: edeefac46805ba74b011d7c86202c7d5dbcdec14
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53367151"
---
# <a name="lesson-1-create-windows-azure-storage-account-and-container"></a>Leçon 1 : Créer un compte et un conteneur Microsoft Azure Storage
  Avant de stocker des fichiers de données SQL Server dans le Stockage Windows Azure, vous devez d'abord créer un compte de stockage Windows Azure et un conteneur d'objets blob, ainsi qu'une signature d'accès partagé. La leçon 1 présente les étapes de connexion au Portail de gestion Windows Azure, puis de création d'un compte de stockage, d'un conteneur d'objets blob et d'une signature d'accès partagé.  
  
 Par défaut, seul le propriétaire du compte de stockage peut accéder aux objets blob, aux tables et aux files d'attente dans ce compte. Pour accéder à ces ressources en utilisant cette nouvelle amélioration SQL Server sans partager la clé d'accès du compte de stockage, effectuez les tâches suivantes :  
  
-   Définissez les autorisations du conteneur avec un accès privé.  
  
-   Créez une signature d'accès partagé. Elle vous permet de déléguer l'accès restreint à un conteneur, à un objet blob, à une table ou à une ressource de file d'attente en spécifiant l'intervalle pendant lequel les ressources sont disponibles et les autorisations dont disposera un client.  
  
-   Utilisez une stratégie d'accès stockée pour gérer les signatures d'accès partagé d'un conteneur ou de ses objets blob. La stratégie d'accès stockée vous donne une mesure supplémentaire de contrôle de vos signatures d'accès partagé et fournit également un moyen simple de les révoquer.  
  
 Pour plus d'informations, consultez [Gérer l'accès aux ressources Microsoft Azure Storage](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).  
  
## <a name="create-storage-account"></a>Créer un compte de stockage  
 Pour créer un compte de stockage sur le Portail de gestion Windows Azure, procédez comme suit :  
  
1.  Connectez-vous au [portail de gestion Microsoft Azure](https://manage.windowsazure.com) à l'aide de votre compte. Si vous ne disposez pas d'un compte Microsoft Azure, [profitez de trois mois d'évaluation gratuite de Microsoft Azure](http://www.windowsazure.com/pricing/free-trial/).  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  Suivez les instructions détaillées pour [créer un compte de stockage](http://azure.microsoft.com/documentation/articles/storage-create-storage-account/). Notez que lorsque vous créez un compte de stockage pour la fonctionnalité Fichiers de données SQL Server dans Windows Azure, vous devez désélectionner ou désactiver la géoréplication. Cela est dû au fait que l'ordre d'écriture n'est pas garanti pour plusieurs objets blob participant à la géoréplication. Si un compte de stockage est géorépliqué et la récupération est requise, une altération se produit.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Créer un conteneur d'objets blob  
 Dans Windows Azure, un conteneur regroupe un ensemble d'objets blob. Tous les objets blob doivent figurer dans un conteneur. Un compte de stockage peut contenir un nombre illimité de conteneurs, mais doit comporter au moins un conteneur. Un conteneur peut stocker un nombre illimité d'objets blob. Pour des informations à jour sur les limites de taille de stockage, consultez [Procédure : utiliser le service de stockage d'objets blob Windows Azure dans le .NET](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Pour créer un conteneur dans Windows Azure, procédez comme suit :  
  
1.  Connectez-vous au [portail de gestion Microsoft Azure](https://manage.windowsazure.com).  
  
2.  Sélectionnez le compte de stockage, cliquez sur l'onglet **Conteneurs** , puis cliquez sur **Ajouter un conteneur** en bas de l'écran pour ouvrir une nouvelle boîte de dialogue.  
  
3.  Entrez le nom du conteneur.  
  
4.  Sélectionnez **Privé** pour le **Type d'accès**. Lorsque vous définissez l'accès privé, le conteneur et les données blob ne peuvent être lus que par le propriétaire du compte Windows Azure.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  Pour créer un conteneur par programme, utilisez également des API REST. Pour plus d'informations, consultez [Créer un conteneur](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) et [Référence de l'API REST des services Microsoft Azure Storage](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).  
  
 **Leçon suivante :**  
  
 [Leçon 2 : Créer une stratégie sur le conteneur et générer une Signature d’accès partagé &#40;SAS&#41; clé](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
  
