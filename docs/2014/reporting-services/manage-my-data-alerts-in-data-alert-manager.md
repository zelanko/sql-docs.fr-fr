---
title: Gérer mes alertes de données dans le Gestionnaire des alertes de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a79771080b1b9c2b7009e7d6228e943e48edbc04
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027100"
---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a>Gérer mes alertes de données dans le Gestionnaire des alertes de données
  Les utilisateurs SharePoint peuvent consulter la liste des alertes de données qu'ils ont créées et les informations sur les alertes. Ils peuvent également supprimer leurs alertes, ouvrir les définitions d'alerte pour les modifier dans le Concepteur d'alertes de données et les exécuter. L'image suivante affiche les fonctionnalités disponibles aux utilisateurs dans le Gestionnaire des alertes de données.  
  
 ![Fonctionnalités du Gestionnaire d’alertes pour les utilisateurs SharePoint](media/rs-alertmanageriw.gif "Fonctionnalités du Gestionnaire d’alertes pour les utilisateurs SharePoint")  
  
### <a name="to-view-a-list-of-your-alerts"></a>Pour consulter la liste de vos alertes  
  
1.  Accédez à la bibliothèque SharePoint où vous avez enregistré les rapports sur lesquels vous avez créé des alertes de données.  
  
2.  Cliquez sur l’icône pour développer le menu déroulant sur un rapport et cliquez sur **Gérer les alertes de données**. L'image suivante montre le menu déroulant.  
  
     ![Ouvrir le Gestionnaire d’alertes à partir du menu contextuel du rapport](media/rs-openalertmanager.gif "Ouvrir le Gestionnaire d’alertes à partir du menu contextuel du rapport")  
  
     Le Gestionnaire des alertes de données s'ouvre. Par défaut, il répertorie les alertes du rapport que vous avez sélectionné dans la bibliothèque.  
  
3.  Cliquez sur la flèche vers le bas en regard de la liste **Afficher les alertes pour le rapport** et sélectionnez un rapport pour consulter ses alertes, ou cliquez sur **Afficher tout** pour répertorier toutes les alertes.  
  
    > [!NOTE]  
    >  Si le rapport que vous avez sélectionné n'a aucune alerte, il n'est pas nécessaire de revenir à la bibliothèque SharePoint pour rechercher et sélectionner un rapport contenant des alertes. Au lieu de cela, cliquez sur **Afficher tout** pour afficher la liste de toutes les alertes.  
  
     Une table répertorie le nom de l'alerte, le nom du rapport, votre nom en tant que créateur de l'alerte, le nombre d'instances d'alerte envoyées, la dernière fois que la définition d'alerte a été modifiée et l'état de l'alerte. Si l'alerte ne peut pas être générée ou envoyée, la colonne d'état contient des informations sur l'erreur et vous aide à dépanner le problème.  
  
### <a name="to-edit-an-alert-definition"></a>Pour modifier une définition d'alerte  
  
-   Cliquez avec le bouton droit sur l’alerte de données que vous souhaitez modifier, puis cliquez sur **Modifier**.  
  
     La définition de l'alerte s'ouvre dans le Concepteur d'alertes de données. Pour plus d’informations, consultez [Modifier une alerte de données dans le Concepteur d’alertes](edit-a-data-alert-in-alert-designer.md) et [Concepteur d’alertes de données](../../2014/reporting-services/data-alert-designer.md).  
  
    > [!NOTE]  
    >  Uniquement l'utilisateur qui a créé la définition d'alerte de données peut la modifier.  
  
    > [!NOTE]  
    >  Si le rapport a changé et les flux de données générés à partir du rapport ont changé, la définition d'alerte peut ne plus être valide. Cela se produit lorsqu'une colonne référencée par l'alerte dans ses règles est supprimée du rapport, change de type de données ou est incluse dans un flux de données différent, ou lorsque le rapport est supprimé ou déplacé. Vous pouvez ouvrir une définition d'alerte non valide, mais vous ne pouvez pas l'enregistrer tant qu'elle n'est pas compatible avec la version actuelle du flux de données du rapport sur lequel elle repose. Pour en savoir plus sur la façon dont les flux de données sont générés à partir des rapports, consultez [Génération de flux de données à partir de rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
### <a name="to-delete-an-alert-definition"></a>Pour supprimer une définition d'alerte  
  
-   Cliquez avec le bouton droit sur l’alerte de données à supprimer, puis cliquez sur **Supprimer**.  
  
     Lorsque vous supprimez l'alerte, aucun message d'alerte n'est envoyé par la suite.  
  
### <a name="to-run-an-alert"></a>Pour exécuter une alerte  
  
-   Cliquez avec le bouton droit sur l’alerte de données à exécuter, puis cliquez sur **Exécuter**.  
  
     L'instance d'alerte est créée et le message d'alerte de données est immédiatement envoyé, quelles que soient les options de planification spécifiées dans le concepteur d'alertes de données. Par exemple, une alerte configurée pour s'exécuter toutes les semaines est envoyée par la suite uniquement si les résultats changent.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire des alertes de données pour les administrateurs d’alertes](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Alertes de données Reporting Services](../ssms/agent/alerts.md)  
  
  
