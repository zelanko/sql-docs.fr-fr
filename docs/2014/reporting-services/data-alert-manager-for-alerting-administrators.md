---
title: Gestionnaire des alertes de données pour les administrateurs d’alertes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 32fd968f-1c0c-4ba8-851c-8a3b5e1fbbf2
caps.latest.revision: 21
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 657ab183836530888773b6709d2efbd75577ee37
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177296"
---
# <a name="data-alert-manager-for-alerting-administrators"></a>Gestionnaire des alertes de données pour les administrateurs d'alertes
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit le Gestionnaire des alertes de données utilisé par les administrateurs d’alertes SharePoint pour gérer des alertes de données. Les administrateurs d'alertes peuvent consulter les informations relatives à toutes les alertes enregistrées sur le site et supprimer des alertes. L'image suivante affiche les fonctionnalités disponibles aux gestionnaires d'alertes SharePoint dans le Gestionnaire des alertes de données.  
  
 ![Gestionnaire d’alertes pour les administrateurs du site SharePoint](media/rs-alertmanagersite.gif "Gestionnaire d’alertes pour les administrateurs du site SharePoint")  
  
 Lorsque le site autorise les alertes de données, deux pages SharePoint, MyDataAlerts.aspx et SiteDataAlerts.aspx sont créées et ajoutées au site SharePoint. SiteDataAlerts.aspx est le Gestionnaire des alertes de données utilisé par les administrateurs d'alertes. Les administrateurs d'alertes peuvent ouvrir le Gestionnaire des alertes de données dans la page Paramètres du site SharePoint. Ils doivent avoir l'autorisation SharePoint de gérer les alertes pour ouvrir le Gestionnaire des alertes de données.  
  
 Vous pouvez également ouvrir directement le Gestionnaire des alertes de données à l'aide d'une URL. L'exemple suivant indique la syntaxe de l'URL.  
  
 `http: //<site name>/_layouts/ReportServer/ SiteDataAlerts.aspx`  
  
> [!NOTE]  
>  En tant qu’administrateur d’alertes, vous pouvez autoriser les travailleurs de l’information à accéder aux fonctionnalités d’alerte de données de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Pour plus d’informations sur les autorisations nécessaires, consultez [Alertes de données Reporting Services](../ssms/agent/alerts.md).  
  
##  <a name="ViewingAlerts"></a> Consulter les informations relatives aux alertes de données  
 Quand Reporting Services est installé et configuré dans SharePoint, la page Paramètres du site SharePoint inclut les options **Reporting Services** . Les administrateurs d’alertes cliquent sur l’option **Gérer les alertes de données** dans Reporting Service pour ouvrir le Gestionnaire des alertes de données. L'image suivante montre à quel endroit de la page Paramètres du site vous ouvrez le Gestionnaire des alertes de données.  
  
 ![Section Reporting Services de la page Paramètres du site](media/rs-sitesettings.gif "Section Reporting Services de la page Paramètres du site")  
  
 Le Gestionnaire des alertes de données inclut une table qui répertorie le nom de l'alerte, le nom du rapport, le nom de la personne qui a créé l'alerte, le nombre de messages d'alerte envoyés, la dernière fois que la définition d'alerte a été exécutée, la dernière fois qu'elle a été modifiée et l'état du message d'alerte. Si l'alerte de données ne peut pas être générée ou envoyée, la colonne d'état contient des informations sur l'erreur et vous aide à dépanner l'alerte. Pour plus d’informations, consultez [gérer toutes les alertes de données sur un SharePoint Site dans le Gestionnaire des alertes de données](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).  
  
 Le tableau suivant présente des exemples de données d'une table dans le Gestionnaire des alertes de données. Quand une erreur se produit, le message d’erreur et l’identificateur de l’entrée du journal (GUID) sont inclus dans le champ **État** de la table.  
  
|Nom de l'alerte|Nom du rapport|Date de création|Alertes envoyées|Dernière exécution|Dernière modification|État|  
|----------------|-----------------|----------------|-----------------|--------------|-------------------|------------|  
|SalesQTR|SalesByTerritoryAndQTR|Lauren Johnson|4|6/12/2011|6/1/2011|La dernière alerte a été exécutée avec succès et l'alerte a été envoyée.|  
|UnitsSold|ProductsSalesByQTR|Michael Blythe|2|7/1/2011|6/28/2011|La dernière alerte a été exécutée avec succès, mais aucune donnée n'a été modifiée et aucune alerte n'a été envoyée.|  
|InventoryCount|StockStatusByQTR|Lauren Johnson|7|7/10/2011|7/2/2011|\<message d’erreur> Le fichier journal contient des informations détaillées sur l’erreur. Consultez l’entrée du journal portant l’identificateur : \<GUID>.|  
|TopPromotion|PromotionTracking|Cristian Petculescu|0||5/23/2011|Alerte créée.|  
  
 Pour plus d’informations, consultez [gérer toutes les alertes de données sur un SharePoint Site dans le Gestionnaire des alertes de données](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).  
  
 Vous pouvez consulter toutes les alertes créées par les utilisateurs du site. Choisissez un utilisateur puis indiquez s'il faut consulter toutes ses alertes ou uniquement celles pour un rapport spécifique.  
  
  
##  <a name="DeleteAlerts"></a> Supprimer des alertes de données  
 Vous pouvez supprimer des définitions d'alerte dans le Gestionnaire des alertes de données. Chaque définition d'alerte de données a un propriétaire, l'utilisateur SharePoint qui l'a créée. Les propriétaires peuvent supprimer uniquement les définitions d'alerte qu'ils ont créées. Pour plus d’informations, consultez [gérer mes alertes de données dans le Gestionnaire des alertes de données](manage-my-data-alerts-in-data-alert-manager.md).  
  
 Un administrateurs d'alertes SharePoint peut répertorier puis supprimer des définitions d'alerte créées par tous les utilisateurs du site. Pour plus d’informations, consultez [gérer toutes les alertes de données sur un SharePoint Site dans le Gestionnaire des alertes de données](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)  
  
 Une fois que vous avez supprimé la définition d'alerte, aucune alerte supplémentaire n'est envoyée. Toutefois, si vous interrogez la base de données des alertes, vous constaterez que la définition d'alerte existe encore. Le service d'alertes effectue un nettoyage planifié qui supprimera définitivement la définition d'alerte lors du nettoyage suivant. L'intervalle de nettoyage par défaut est de 20 minutes. Cet intervalle, ainsi que d'autres paramètres de nettoyage, sont configurables. Pour plus d’informations, consultez [Alertes de données Reporting Services](../ssms/agent/alerts.md).  
  
  
##  <a name="HowTo"></a> Tâches associées  
 Cette section décrit la procédure qui vous explique comment gérer vos alertes.  
  
-   [Gérer toutes les alertes de données sur un site SharePoint dans le gestionnaire des alertes de données](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)  
  
  
## <a name="see-also"></a>Voir aussi  
 [Alertes de données Reporting Services](../ssms/agent/alerts.md)  
  
  
