---
title: "G&#233;rer toutes les alertes de donn&#233;es sur un site SharePoint dans le Gestionnaire des alertes de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestion, alertes"
  - "gestion, alertes de données"
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 13
---
# G&#233;rer toutes les alertes de donn&#233;es sur un site SharePoint dans le Gestionnaire des alertes de donn&#233;es
  Les administrateurs d'alertes SharePoint peuvent consulter la liste des alertes de données que tous les utilisateurs du site ont créées et les informations sur les alertes. Ils peuvent également supprimer des alertes. L'illustration suivante montre les fonctionnalités disponibles aux administrateurs d'alertes dans le Gestionnaire des alertes de données.  
  
 ![Gestionnaire d'alertes pour les administrateurs du site SharePoint](../reporting-services/media/rs-alertmanagersite.gif "Gestionnaire d'alertes pour les administrateurs du site SharePoint")  
  
### Pour consulter la liste des alertes créées par un utilisateur du site  
  
1.  Accédez au site SharePoint où les définitions d'alertes de données sont enregistrées.  
  
2.  Dans la page d’accueil, cliquez sur **Actions de site**.  
  
3.  Faites défiler jusqu’au fond de la liste et cliquez sur **Paramètres du site**.  
  
4.  Sous **Reporting Services**cliquez sur **Gérer les alertes de données**.  
  
5.  Cliquez sur la flèche vers le bas dans la liste **Afficher les alertes pour l’utilisateur** et sélectionnez l’utilisateur dont vous souhaitez afficher les alertes.  
  
6.  Cliquez sur la flèche vers le bas en regard de la liste **Afficher les alertes pour le rapport** et sélectionnez une alerte spécifique ou cliquez sur **Afficher tout** pour répertorier toutes les alertes créées par l’utilisateur sélectionné.  
  
     Une table répertorie le nom de l'alerte, le nom du rapport, le nom de la personne qui a créé l'alerte de données, le nombre de fois que l'alerte de données a été envoyée, la dernière fois que la définition d'alerte de données a été modifiée et l'état de l'alerte de données. Si l'alerte de données ne peut pas être générée ou envoyée, la colonne d'état contient des informations sur l'erreur et vous aide à dépanner le problème.  
  
### Pour supprimer une définition d'alerte  
  
-   Cliquez avec le bouton droit sur l’alerte de données à supprimer, puis cliquez sur **Supprimer**.  
  
    > [!NOTE]  
    >  Une fois que vous avez supprimé l’alerte, aucun message d’alerte n’est envoyé. Toutefois, si vous interrogez la base de données des alertes, vous constaterez que la définition d'alerte existe encore. Le service d'alertes effectue un nettoyage planifié qui supprimera définitivement la définition d'alerte lors du nettoyage suivant. L'intervalle de nettoyage par défaut est de 20 minutes. Cet intervalle, ainsi que d'autres paramètres de nettoyage, sont configurables. Pour plus d’informations, consultez [Alertes de données Reporting Services](../reporting-services/reporting-services-data-alerts.md).  
  
## Voir aussi  
 [Gestionnaire des alertes de données pour les administrateurs d'alertes](../reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Alertes de données Reporting Services](../reporting-services/reporting-services-data-alerts.md)  
  
  