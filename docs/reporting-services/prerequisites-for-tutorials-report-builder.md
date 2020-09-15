---
title: Prérequis pour les didacticiels (Générateur de rapports) | Microsoft Docs
description: Découvrez les prérequis dont vous avez besoin pour suivre les tutoriels relatifs au Générateur de rapports.
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 15ca9251c5cb9f541710d7a18b8c10864cd24b8c
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87945515"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Éléments requis pour les didacticiels (Générateur de rapports)

L’utilisation des didacticiels du Générateur de rapports suppose que vous pouvez afficher et enregistrer des rapports paginés [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] sur un serveur de rapports ou un site SharePoint intégré à un serveur de rapports. Pour les données, tous les didacticiels utilisent des requêtes littérales qui doivent être traitées par une instance de SQL Server.  
  
Si vous n'avez pas accès à un serveur de rapports, un site de serveur de rapports ou une source de données, vous pouvez en apprendre plus sur le Générateur de rapports en générant un rapport hors connexion. Voir le [tutoriel : Créer un rapport de graphique rapide en mode hors connexion &#40;Générateur de rapports&#41;](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  

## <a name="requirements"></a>Spécifications

Pour exécuter les didacticiels du Générateur de rapports, vous devez réunir les conditions suivantes :  
  
-   Accès au Générateur de rapports. Vous pouvez exécuter le Générateur de rapports depuis un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] ou un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] en mode intégré SharePoint. Seule la première étape, l’ouverture du Générateur de rapports, varie selon les différents serveurs.  
  
    Sur un serveur de rapports, sélectionnez **Nouveau** > **Rapport paginé**.
  
    Sur un serveur de rapports en mode intégré SharePoint, sous l’onglet **Documents** , sélectionnez **Nouveau Document**et, dans la liste déroulante, sélectionnez **Rapport du Générateur de rapports**. Par exemple : `https://<servername>/sites/mySite/reports`. L'administrateur SharePoint doit activer la fonctionnalité Rapport du Générateur de rapports pour chaque bibliothèque de documents.  
  
-   URL pointant vers un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] ou un site SharePoint intégré à un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] . Vous devez être autorisé à enregistrer et consulter des rapports, des sources de données partagées, des datasets partagés, des parties de rapports et des modèles. Par défaut, l’URL d’un serveur de rapports est `https://<servername>/reportserver`. Par défaut, l’URL d’un site SharePoint est `https://<sitename>` ou `https://<server>/site`.  
  
-   Nom d’une instance de SQL Server et des informations d’identification suffisantes pour l’accès en lecture seule à n’importe quelle base de données. Les requêtes de dataset des didacticiels utilisent des données littérales, mais chaque requête doit être traitée par une instance de SQL Server pour retourner les métadonnées nécessaires à un dataset de rapport. Par exemple, la chaîne de connexion suivante spécifie uniquement un serveur : `data source=<servername>`. Vous devez avoir un accès en lecture à la base de données par défaut qui vous est affectée par l'administrateur système qui vous accorde l'autorisation d'accès au serveur. Vous pouvez également spécifier une base de données, comme indiqué dans la chaîne de connexion suivante : `data source=<servername>;initial catalog=<database>`.  
  
-   Pour le [tutoriel : Rapport cartographique (Générateur de rapports)](tutorial-map-report-report-builder.md), le serveur de rapports doit être configuré pour prendre en charge les cartes Bing comme arrière-plan. Pour plus d’informations, consultez [Planifier la prise en charge de rapport cartographique](https://docs.microsoft.com/sql/reporting-services/report-design/plan-a-map-report-report-builder-and-ssrs).   

-   Le [Tutoriel : La création d’un rapport principal et d’un rapport d’extraction (Générateur de rapports)](tutorial-creating-drillthrough-and-main-reports-report-builder.md) nécessite un accès au cube Contoso Sales. Pour plus d’informations, consultez le didacticiel. 
  
L’administrateur du serveur de rapports doit vous accorder les autorisations nécessaires sur le serveur de rapports, configurer les emplacements des dossiers [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] et configurer les options par défaut du Générateur de rapports. Pour plus d’informations, consultez [Install Report Builder](install-windows/install-report-builder.md).  

## <a name="next-steps"></a>Étapes suivantes

[Didacticiels du Générateur de rapports](../reporting-services/report-builder-tutorials.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
