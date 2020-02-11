---
title: Prérequis pour les didacticiels (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 17c8b67d29cb82956a37bc3f83867161486a4f9e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73637862"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Éléments requis pour les didacticiels (Générateur de rapports)
  L'utilisation des didacticiels du Générateur de rapports suppose que vous puissiez afficher et enregistrer des rapports sur un serveur de rapports ou un site SharePoint intégré à un serveur de rapports. Pour les données, tous les didacticiels utilisent des requêtes littérales qui doivent être traitées par une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Si vous n'avez pas accès à un serveur de rapports, un site de serveur de rapports ou une source de données, vous pouvez en apprendre plus sur le Générateur de rapports en générant un rapport hors connexion. Consultez [Didacticiel : créer un rapport de graphique rapide en mode hors connexion &#40;Générateur de rapports&#41;](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## <a name="requirements"></a>Spécifications  
 Pour exécuter les didacticiels du Générateur de rapports, vous devez réunir les conditions suivantes :  
  
-   Accès aux [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] générateur de rapports. Vous pouvez exécuter le Générateur de rapports à l'aide de la version autonome ou la version ClickOnce du Générateur de rapports, disponible depuis le Gestionnaire de rapports ou un site SharePoint. Seule la première étape, l'ouverture du Générateur de rapports, est différente pour les versions ClickOnce.  
  
     Pour utiliser Gestionnaire de rapports, ouvrez Gestionnaire de rapports puis cliquez sur **Générateur de rapports**. Par défaut, l’URL de gestionnaire de rapports est http://\<*ServerName*>/Reports.  
  
     Pour utiliser un site SharePoint, naviguez jusqu'au site, cliquez sur l'onglet Documents, cliquez sur Nouveau document, puis cliquez dans la liste déroulante sur Rapport du Générateur de rapports. Par exemple, http://\<ServerName>/sites/mysite/Reports. L'administrateur SharePoint doit activer la fonctionnalité Rapport du Générateur de rapports pour chaque bibliothèque de documents.  
  
-   URL pointant vers un serveur de rapports [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] ou un site SharePoint intégré à un serveur de rapports [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] . Vous devez être autorisé à enregistrer et consulter des rapports, des sources de données partagées, des datasets partagés, des parties de rapports et des modèles. Par défaut, l’URL d’un serveur de rapports est\<http://servername>/ReportServer. Par défaut, l’URL d’un site SharePoint est http://\<SiteName> ou http://\<Server>/site.  
  
-   Nom d’une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et des informations d’identification suffisantes pour l’accès en lecture seule à n’importe quelle base de données. Les requêtes de dataset des didacticiels utilisent des données littérales, mais chaque requête doit être traitée par une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] pour retourner les métadonnées nécessaires à un dataset de rapport. Par exemple, la chaîne de connexion suivante spécifie uniquement un serveur : `data source=<servername>`. Vous devez avoir un accès en lecture à la base de données par défaut qui vous est affectée par l'administrateur système qui vous accorde l'autorisation d'accès au serveur. Vous pouvez également spécifier une base de données, comme indiqué dans la chaîne de connexion suivante : `data source=<servername>;initial catalog=<database>`.  
  
-   Pour le didacticiel qui inclut une carte, le serveur de rapports doit être configuré pour prendre en charge les cartes Bing en tant qu'arrière-plan. Pour plus d’informations, consultez [planifier la prise en charge des rapports cartographiques](plan-for-map-report-support.md) dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] la documentation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la documentation [en ligne](https://go.microsoft.com/fwlink/?LinkId=154888) de sur MSDN.Microsoft.com.  
  
-   Le didacticiel, [Didacticiel : création d’une extraction et de rapports principaux &#40;Générateur de rapports&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md), utilise le jeu de données de démonstration Business Intelligence de contoso. Ce dataset se compose de l'entrepôt de données ContosoDW et de la base de données de traitement analytique en ligne (OLAP) Contoso_Retail. Les rapports que vous allez créer dans ce didacticiel récupèrent des données du cube Contoso Sales. Vous pouvez télécharger la base de données OLAP Contoso_Retail à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=18279). Il vous suffit de télécharger le fichier ContosoBIdemoABF.exe. Il contient la base de données OLAP.  
  
     L'autre fichier, ContosoBIdemoBAK.exe, concerne l'entrepôt de données ContosoDW, qui n'est pas utilisé dans ce didacticiel.  
  
     Le site Web comporte des instructions relatives à l'extraction et à la restauration du fichier de sauvegarde ContosoRetail.abf dans la base de données OLAP Contoso_Retail.  
  
     Vous devez accéder à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur laquelle installer la base de données OLAP.  
  
 L’administrateur du serveur de rapports doit vous accorder les autorisations nécessaires sur le serveur de rapports, configurer les emplacements des dossiers [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] et configurer les options par défaut du Générateur de rapports. Pour plus d’informations, consultez [installation, désinstallation et prise en charge de générateur de rapports](install-uninstall-and-report-builder-support.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)  
  
  
