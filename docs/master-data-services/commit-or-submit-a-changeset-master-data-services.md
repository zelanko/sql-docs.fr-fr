---
title: Valider ou envoyer un ensemble de modifications (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d323bbac-c8d4-4d2f-a7d2-a597e8b53e2d
caps.latest.revision: "10"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 81f34bc5c33210a4e350869e085d491222512858
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="commit-or-submit-a-changeset-master-data-services"></a>Valider ou envoyer un ensemble de modifications (Master Data Services)
  Un ensemble de modifications est un ensemble de modifications en attente portant sur les données de référence. Si les modifications apportées à une entité ne nécessitent pas l’approbation de l’administrateur, vous pouvez valider l’ensemble de modifications. Si les modifications apportées à une entité nécessitent l’approbation de l’administrateur, vous pouvez envoyer l’ensemble de modifications pour approbation.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** . Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Si les modifications apportées à une entité ne nécessitent pas l’approbation de l’administrateur, vous pouvez valider l’ensemble de modifications uniquement si vous possédez l’ensemble de modifications et si l’état de l’ensemble de modifications est ouvert.  
  
-   Si les modifications apportées à une entité nécessitent l’approbation de l’administrateur, vous pouvez envoyer l’ensemble de modifications pour approbation uniquement si vous possédez l’ensemble de modifications et si l’état de l’ensemble de modifications est ouvert ou rejeté.  
  
## <a name="to-commit-a-local-changeset"></a>Pour valider un ensemble de modifications local  
 L’option de validation n’est disponible pour les ensembles de modifications locaux que sur les entités où l’administrateur d’entité n’a pas activé la nécessité d’approbation.  
  
1.  Sur la page d’accueil [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , sélectionnez le modèle et la version, puis cliquez sur **Explorateur**.  
  
2.  Dans le menu **Entités** , cliquez sur une entité.  
  
3.  Dans le volet droit, sélectionnez **Ensembles de modifications** , puis double-cliquez sur l’ensemble de modifications à valider.  
  
4.  Cliquez sur **Valider**.  
  
## <a name="to-submit-a-changeset"></a>Pour envoyer un ensemble de modifications  
 L’option d’envoi n’est disponible pour les ensembles de modifications que sur les entités où l’administrateur d’entité a activé la nécessité d’approbation.  
  
1.  Sur la page d’accueil [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , sélectionnez le modèle et la version, puis cliquez sur **Explorateur**.  
  
2.  Dans le menu **Entités** , cliquez sur une entité.  
  
3.  Dans le volet droit, sélectionnez **Ensembles de modifications** , puis double-cliquez sur l’ensemble de modifications à envoyer.  
  
4.  Cliquez sur **Envoyer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Approuver ou rejeter un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Appliquer et mettre à jour un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Approuver ou rejeter un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
