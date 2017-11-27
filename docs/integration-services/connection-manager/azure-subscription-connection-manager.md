---
title: "Gestionnaire de connexions d’abonnement Azure | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpsubscrconn.f1
- sql14.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f34ac8d5c1b6bd117a83d287db1d46ff6f786aab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="azure-subscription-connection-manager"></a>Gestionnaire de connexions d’abonnement Azure
  Le **gestionnaire de connexions d’abonnement Azure** permet à un package SSIS de se connecter à un abonnement Azure en utilisant les valeurs spécifiées pour les propriétés : ID d’abonnement Azure et certificat de gestion.  
  
 Le **Gestionnaire de connexions d’abonnement Azure** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
1.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** ci-dessus, sélectionnez **Abonnement Azure**, puis cliquez sur **Ajouter**.  Vous devez voir s’afficher la boîte de dialogue **Éditeur du gestionnaire de connexions d’abonnement Azure** .  
  
    ![SSIS-AzureSubscriptionConnectionManager](../../integration-services/connection-manager/media/ssis-azuresubscriptionconnectionmanager.png)
  
2.  Entrez votre ID d’abonnement Azure, qui identifie de façon unique un abonnement Azure, pour l’ **ID d’abonnement Azure**.  Cette valeur est indiquée sur le [portail de gestion Azure](https://manage.windowsazure.com) , à la page **Paramètres** :  
  
    ![SSIS AzureSettings ID d’abonnement](../../integration-services/connection-manager/media/ssis-azuresettings-subscriptionid.png "SSIS AzureSettings ID d’abonnement")  
  
3.  Choisissez **Emplacement du magasin de certificats de gestion** et **Nom du magasin de certificats de gestion** dans les listes déroulantes.  
  
4.  Entrez l’ **empreinte numérique du certificat de gestion** ou cliquez sur **Parcourir** pour choisir un certificat dans le magasin sélectionné. Le certificat doit être téléchargé en tant que certificat de gestion pour l’abonnement. Pour ce faire, cliquez sur **Télécharger** dans la page suivante du portail Azure (voir cet [article MSDN](https://msdn.microsoft.com/library/azure/gg551722.aspx) pour plus de détails).  
  
     ![Un certificat de AzureSettings gestion SSIS](../../integration-services/connection-manager/media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-un certificat de gestion")  
  
5.  Cliquez sur **Tester la connexion** pour tester la connexion.  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
  

