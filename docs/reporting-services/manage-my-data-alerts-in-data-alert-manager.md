---
title: "Gérer mes alertes de données dans le Gestionnaire des alertes de données | Documents Microsoft"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: fdea7fc38d680e8bf7acb104254cb75b95297660
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a>Gérer mes alertes de données dans le Gestionnaire des alertes de données

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../includes/ssrs-appliesto-sql2016-xpreview.md)][!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

Les utilisateurs SharePoint peuvent consulter la liste des alertes de données qu'ils ont créées et les informations sur les alertes. Ils peuvent également supprimer leurs alertes, ouvrir les définitions d'alerte pour les modifier dans le Concepteur d'alertes de données et les exécuter. L'image suivante affiche les fonctionnalités disponibles aux utilisateurs dans le Gestionnaire des alertes de données.

 ![Fonctionnalités du gestionnaire pour les utilisateurs SharePoint d’alerte](../reporting-services/media/rs-alertmanageriw.gif "des fonctionnalités de gestionnaire d’alertes pour les utilisateurs SharePoint")

> [!NOTE]
> Intégration de Reporting Services avec SharePoint n’est plus disponible après SQL Server 2016.

### <a name="to-view-a-list-of-your-alerts"></a>Pour consulter la liste de vos alertes  
  
1.  Accédez à la bibliothèque SharePoint où vous avez enregistré les rapports sur lesquels vous avez créé des alertes de données.  
  
2.  Cliquez sur l’icône pour développer le menu déroulant sur un rapport et cliquez sur **Gérer les alertes de données**. L'image suivante montre le menu déroulant.  
  
     ![Ouvrez le Gestionnaire des alertes à partir du menu contextuel du rapport](../reporting-services/media/rs-openalertmanager.gif "Ouvrez Gestionnaire des alertes à partir du menu contextuel du rapport")  
  
     Le Gestionnaire des alertes de données s'ouvre. Par défaut, il répertorie les alertes du rapport que vous avez sélectionné dans la bibliothèque.  
  
3.  Cliquez sur la flèche vers le bas en regard de la liste **Afficher les alertes pour le rapport** et sélectionnez un rapport pour consulter ses alertes, ou cliquez sur **Afficher tout** pour répertorier toutes les alertes.  
  
    > [!NOTE]  
    >  Si le rapport que vous avez sélectionné n'a aucune alerte, il n'est pas nécessaire de revenir à la bibliothèque SharePoint pour rechercher et sélectionner un rapport contenant des alertes. Au lieu de cela, cliquez sur **Afficher tout** pour afficher la liste de toutes les alertes.  
  
     Une table répertorie le nom de l'alerte, le nom du rapport, votre nom en tant que créateur de l'alerte, le nombre d'instances d'alerte envoyées, la dernière fois que la définition d'alerte a été modifiée et l'état de l'alerte. Si l'alerte ne peut pas être générée ou envoyée, la colonne d'état contient des informations sur l'erreur et vous aide à dépanner le problème.  
  
### <a name="to-edit-an-alert-definition"></a>Pour modifier une définition d'alerte  
  
-   Cliquez avec le bouton droit sur l’alerte de données que vous souhaitez modifier, puis cliquez sur **Modifier**.  
  
     La définition de l'alerte s'ouvre dans le Concepteur d'alertes de données. Pour plus d’informations, consultez [Modifier une alerte de données dans le Concepteur d’alertes](../reporting-services/edit-a-data-alert-in-alert-designer.md) et [Concepteur d’alertes de données](../reporting-services/data-alert-designer.md).  
  
    > [!NOTE]  
    >  Uniquement l'utilisateur qui a créé la définition d'alerte de données peut la modifier.  
  
    > [!NOTE]  
    >  Si le rapport a changé et les flux de données générés à partir du rapport ont changé, la définition d'alerte peut ne plus être valide. Cela se produit lorsqu'une colonne référencée par l'alerte dans ses règles est supprimée du rapport, change de type de données ou est incluse dans un flux de données différent, ou lorsque le rapport est supprimé ou déplacé. Vous pouvez ouvrir une définition d'alerte non valide, mais vous ne pouvez pas l'enregistrer tant qu'elle n'est pas compatible avec la version actuelle du flux de données du rapport sur lequel elle repose. Pour en savoir plus sur la façon dont les flux de données sont générés à partir des rapports, consultez [Génération de flux de données à partir de rapports &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
### <a name="to-delete-an-alert-definition"></a>Pour supprimer une définition d'alerte  
  
-   Cliquez avec le bouton droit sur l’alerte de données à supprimer, puis cliquez sur **Supprimer**.  
  
     Lorsque vous supprimez l'alerte, aucun message d'alerte n'est envoyé par la suite.  
  
### <a name="to-run-an-alert"></a>Pour exécuter une alerte  
  
-   Cliquez avec le bouton droit sur l’alerte de données à exécuter, puis cliquez sur **Exécuter**.  
  
     L'instance d'alerte est créée et le message d'alerte de données est immédiatement envoyé, quelles que soient les options de planification spécifiées dans le concepteur d'alertes de données. Par exemple, une alerte configurée pour s'exécuter toutes les semaines est envoyée par la suite uniquement si les résultats changent.  

## <a name="see-also"></a>Voir aussi

[Gestionnaire des alertes de données pour les administrateurs d'alertes](../reporting-services/data-alert-manager-for-alerting-administrators.md)   
[Alertes de données Reporting Services](../reporting-services/reporting-services-data-alerts.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
