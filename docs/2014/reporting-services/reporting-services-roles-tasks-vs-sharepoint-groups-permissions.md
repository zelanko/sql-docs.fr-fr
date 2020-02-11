---
title: Comparer des rôles et des tâches dans Reporting Services à des groupes et des autorisations SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- security [Reporting Services], tasks
- roles [Reporting Services], predefined
- SharePoint integration [Reporting Services], permissions
- permissions [Reporting Services], native mode
- security [Reporting Services], predefined roles
- security [Reporting Services], SharePoint integrated mode
ms.assetid: 429f1dbb-183a-4097-bd1b-693da9fe7a36
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c56b15a5d6887c3e00047c9a0c3a66f907ef468
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66102811"
---
# <a name="compare-roles-and-tasks-in-reporting-services-to-sharepoint-groups-and-permissions"></a>Comparer des rôles et des tâches dans Reporting Services avec les autorisations et les groupes SharePoint
  Cette rubrique compare les fonctionnalités d'autorisation basées sur les rôles et les tâches en mode natif [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aux fonctionnalités de sécurité dans les produits SharePoint. Cette rubrique compare la terminologie et les caractéristiques des rôles, des tâches, des groupes SharePoint, des niveaux d'autorisation et des autorisations.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)]<br /><br /> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Mode SharePoint &#124; SharePoint 2010 et SharePoint 2013<br /><br /> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Mode natif|  
  
 **Dans cette rubrique :**  
  
-   [Comparer les outils et la terminologie des autorisations](#bkmk_compare_tools_terms)  
  
-   [Comparer les rôles en mode natif et les groupes SharePoint](#bkmk_compare_roles_groups)  
  
-   [Comparaison des tâches en mode natif et des autorisations SharePoint](#bkmk_compare_tasks_permissions)  
  
##  <a name="bkmk_compare_tools_terms"></a>Comparer les outils et la terminologie des autorisations  
 **Mode natif :** Les [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] objets d’autorisation en mode natif (rôles et tâches) sont [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] créés dans et configurés pour des utilisateurs individuels dans Gestionnaire de rapports.  
  
 **Mode SharePoint :** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] le mode SharePoint utilise les fonctionnalités d’autorisation SharePoint. Les groupes et les autorisations SharePoint sont gérés depuis la page **Paramètres du site** .  
  
 Le tableau suivant compare des objets et les concepts liés aux autorisations entre le mode natif [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et SharePoint.  
  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Mode natif|SharePoint|  
|---------------------------------------------|----------------|  
|**Rôle :** Par exemple, « gestionnaire de contenu ».|**Groupe :** Par exemple, le groupe « visionneuses » par défaut.|  
|---|**Groupe de niveau d’autorisation :** Par exemple, « afficher uniquement » pour le groupe « visionneuses ».|  
|**Tâches :** par exemple, « gérer les rapports ».|**Autorisations :** Par exemple, dans le groupe « Afficher uniquement », il existe des autorisations relatives à la liste des éléments d’affichage, des versions de vue et des pages d’application de vue.|  
  
 Pour plus d’informations sur les autorisations SharePoint, consultez [autorisations utilisateur et niveaux d’autorisation dans SharePoint Server](/sharepoint/sites/user-permissions-and-permission-levels) et [déterminer les niveaux d’autorisation et les groupes dans SharePoint 2013](https://technet.microsoft.com/library/cc262690.aspx).  
  
##  <a name="bkmk_compare_roles_groups"></a>Comparer les rôles en mode natif et les groupes SharePoint  
 Le tableau suivant compare les définitions de rôles prédéfinies dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif aux groupes SharePoint standard. Si les groupes SharePoint ne correspondent pas au rôle spécifique que vous recherchez, vous pouvez créer un groupe personnalisé et attribuer des niveaux d'autorisation dans SharePoint.  
  
 **Remarque**: les groupes SharePoint par défaut disponibles dépendent du modèle de site utilisé pour créer le site SharePoint.  
  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Actif|Groupes SharePoint|  
|--------------------------------------|-----------------------|  
|**Browser**<br /><br /> Affichage|Utilisez le groupe **Visiteurs** pour accorder des autorisations pour afficher des rapports. Le groupe **Visiteurs** possède les autorisations de niveau Lecture qui permettent aux membres du groupe d'afficher des pages, des éléments de liste et des documents.|  
|**Gestionnaire de contenu**<br /><br /> Autorisations complètes à tous les éléments et opérations au niveau élément, et notamment les autorisations de définir la sécurité.|Utilisez le groupe **Propriétaires** pour accorder le contrôle total sur la gestion des éléments de serveur de rapports sur un site SharePoint. Le groupe **Propriétaires** possède les autorisations Contrôle total qui permettent aux membres du groupe d'apporter des modifications au contenu, aux pages ou aux fonctionnalités du site. L'accès Contrôle total doit être limité aux administrateurs de site uniquement.|  
|**Mes rapports**|Il n'y a pas de groupe équivalent. **Mes rapports** n’est pas pris en charge pour un serveur de rapports qui s’exécute en mode SharePoint. Vous pouvez utiliser les fonctionnalités relatives à Mon Site dans [!INCLUDE[winSPServ](../includes/winspserv-md.md)] si vous souhaitez utiliser des fonctionnalités équivalentes.|  
|**Publisher**<br /><br /> Ajoutez, mettez à jour, affichez et supprimez des rapports, des modèles de rapport, des sources de données partagées et des ressources.|Utilisez le groupe **Membres** pour accorder des autorisations d'ajouter des éléments, de modifier des éléments et de mettre à jour des références à des éléments dépendants sur un site SharePoint. Le groupe **Membres** possède les autorisations de niveau Collaboration qui permettent aux membres du groupe d'afficher des pages, d'ajouter et de mettre à jour des éléments, de soumettre à l'approbation des modifications.|  
|**Générateur de rapports**<br /><br /> Affichez des rapports, auto-gérez des abonnements individuels et ouvrez des rapports dans le Générateur de rapports.|Il n'existe pas de niveau d'autorisation prédéfini ou de groupe SharePoint équivalent à la définition de rapport du Générateur de rapports. Par défaut, les utilisateurs qui appartiennent aux groupes **Membres** ou **Propriétaires** sont autorisés à utiliser le Générateur de rapports. Si vous souhaitez élargir l'accès du Générateur de rapports à davantage d'utilisateurs, vous devez créer des paramètres de sécurité personnalisés pour fournir un niveau d'autorisation similaire à celui fourni par le rôle de Générateur de rapports. Pour plus d’information, consultez [Définir les autorisations sur les éléments du serveur de rapports sur un site SharePoint &#40;Reporting Services en mode intégré SharePoint&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md).|  
|-|Utilisez le groupe **Visionneuses** pour accorder des autorisations pour afficher des rapports rendus. Le groupe **Visionneuses** ne peut pas télécharger ou afficher le contenu d'éléments de rapport.<br /><br /> **Remarque :** À compter de SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]2012, le groupe **observateurs** ne dispose pas des autorisations nécessaires pour créer des abonnements.|  
|**Utilisateur système** et **administrateur système**|Ces rôles ne sont pas nécessaires pour un serveur de rapports qui s'exécute en mode SharePoint. L' **utilisateur système** et l' **administrateur système** correspondent à des autorisations de niveau application Web ou batterie de serveurs SharePoint. Le serveur de rapports ne fournit pas de fonctionnalités qui nécessitent des autorisations à ce niveau.|  
  
##  <a name="bkmk_compare_tasks_permissions"></a>Comparaison des tâches en mode natif et des autorisations SharePoint  
 Le tableau suivant compare les tâches [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif aux autorisations SharePoint. La colonne **Type** indique si la tâche en mode natif est associée à un rôle système ou à un rôle et des éléments standard. Les rôles système gèrent les autorisations au niveau du système, par exemple les planifications partagées.  
  
|Tâche en mode natif|Type de rôle|Autorisation SharePoint équivalente|  
|----------------------|---------------|--------------------------------------|  
|Lire les rapports|Élément|Modifier les éléments, Afficher les éléments.|  
|Créer des rapports liés|Élément|Non pris en charge.|  
|Gérer tous les abonnements|Élément|Gérer les alertes.|  
|Gérer les sources de données|Élément|Ajouter les éléments, Modifier les éléments, Supprimer les éléments, Afficher les éléments.|  
|Gérer les dossiers|Élément|Ajouter les éléments, Modifier les éléments, Supprimer les éléments, Afficher les éléments.|  
|Gérer les abonnements individuels|Élément|Modifier des éléments<br /><br /> Avant [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], le niveau d'autorisation requis était Créer des alertes.|  
|Gérer les modèles|Élément|Ajouter les éléments, Modifier les éléments, Supprimer les éléments, Afficher les éléments.|  
|Gérer l'historique de rapport|Élément|Modifier les éléments, Afficher les versions, Supprimer les versions.|  
|Gérer les rapports|Élément|Ajouter les éléments, Modifier les éléments, Supprimer les éléments, Afficher les éléments.|  
|Gestion des ressources|Élément|Ajouter les éléments, Modifier les éléments, Supprimer les éléments, Afficher les éléments.|  
|Définir la sécurité pour des éléments individuels|Élément|Gérer les autorisations|  
|Afficher les sources de données|Élément|Afficher les éléments.|  
|Afficher les dossiers|Élément|Afficher les éléments.|  
|Afficher les modèles|Élément|Afficher les éléments.|  
|Afficher les rapports|Élément|Afficher les éléments.|  
|Afficher les ressources|Élément|Afficher les éléments.|  
||||  
|Exécuter les définitions de rapport|Système|Afficher les éléments.|  
|Générer des événements|Système|Gérer le site Web.|  
|Gestion des travaux|Système|Aucun (non pris en charge).|  
|Gérer les propriétés du serveur de rapports|Système|Aucun (non applicable). Le serveur de rapports ne détermine pas si un utilisateur est autorisé à consulter les paramètres d'intégration dans l'administration centrale.|  
|Gérer les rôles|Système|Gérer les autorisations.|  
|Gérer les planifications partagées|Système|Gérer le site Web, ouvrir.|  
|Gérer la sécurité du serveur de rapports|Système|Aucun (non applicable). Le rapport de serveurs n'utilise pas d'attributions de rôle au niveau du système sur un serveur qui s'exécute en mode intégré SharePoint.|  
|Afficher les propriétés du serveur de rapports|Système|Aucun (non applicable). Le serveur de rapports ne détermine pas si un utilisateur est autorisé à consulter les paramètres d'intégration dans l'administration centrale.|  
|Afficher les planifications partagées|Système|Ouvrir les éléments.|  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des autorisations pour les éléments de serveur de rapports sur un site SharePoint &#40;Reporting Services en mode intégré SharePoint&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)   
 [Définir des autorisations pour des opérations de serveurs de rapports dans une application web SharePoint](security/set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md)   
 [Accord d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Définitions de rôles](security/role-definitions.md)   
 [Rôles prédéfinis](security/role-definitions-predefined-roles.md)  
  
  
