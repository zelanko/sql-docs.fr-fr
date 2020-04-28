---
title: Analyse et création de rapports avec les outils Microsoft Business Intelligence
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 7c76ec1a74032b5f35bc42ab4a901d95574e0900
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75688214"
---
# <a name="analysis-and-reporting-with-microsoft-business-intelligence-bi-tools"></a>Analyse et création de rapports avec les outils Microsoft Business Intelligence

  Le tableau suivant mappe les charges de travail pour l'analyse et la création de rapports de données aux outils Microsoft BI qui sont le mieux adaptés à ces charges de travail.  
  
 L'objectif est de vous aider à choisir l'outil qui correspond le mieux à vos besoins. Pour plus d'informations sur un produit, cliquez sur le lien correspondant dans la table.  
  
 Pour obtenir une brève présentation de ces outils et choisir ceux qui vous conviennent le mieux, consultez [Introducing Microsoft Business Intelligence (BI) Tools](https://www.digitalvidya.com/blog/introduction-to-microsoft-power-bi/).  
  
|Charges de travail|Utilisateur|||Outils BI|||  
|---------------|----------|-|-|--------------|-|-|  
|||**Excel**|**SharePoint**|**SharePoint Online**|**Power BI**|**SQL Server**|  
|**BI en libre-service**|Analyste/Utilisateur final||||||  
|Découvrir facilement et accéder à des données publiques et d'entreprise||[Power Query](https://go.microsoft.com/fwlink/p/?LinkId=391845)||[Azure Data Catalog](https://azure.microsoft.com/services/data-catalog/)<br /><br />||  
|Créer des modèles de données puissants||[Power Pivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed?ui=en-US&rs=en-US&ad=US)|||[Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-get-the-desktop/)||  
|Effectuer des analyses prédictives en libre-service||||||[Compléments d'exploration de données pour Excel](../analysis-services/data-mining-client-for-excel-sql-server-data-mining-add-ins.md)|  
|Visualiser et explorer les données||[Power View](https://go.microsoft.com/fwlink/p/?LinkId=391847)<br /><br /> [Cartes 3D](https://support.office.com/article/visualize-your-data-in-3d-maps-ce6b1d5c-4602-4dae-b487-91ec0268e75d)|||||  
|Poser des questions à l'aide d'un requête en langage naturel|||||[Q & A](https://docs.microsoft.com/power-bi/consumer/end-user-q-and-a)||  
|Accéder à des rapports avec des appareils mobiles||||[HTML 5 (prend en charge l’affichage des fichiers <10 Mo)](https://go.microsoft.com/fwlink/p/?LinkId=391853)|[HTML 5 (prend en charge l’affichage < 250 Mo)](https://go.microsoft.com/fwlink/p/?LinkId=391854)<br /><br /> [Application mobile Power BI sur les appareils iOS](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-iphone-app-get-started)<br /><br /> [Application mobile Power BI sur les appareils Android](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-android-app-get-started) <br /><br />[Application mobile Power BI pour Windows 10](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-windows-10-phone-app-get-started)||  
|Collaborer et partager|||[Sites SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=391849)|[Sites de l'équipe SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=391850)|[Sites Power BI](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports)||  
|**BI d'entreprise**|Professionnel de l'informatique||||||  
|Créer des modèles d'entreprise multidimensionnels/tabulaires||||||[Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services-overview)|  
|Créer des visualisations de données ad-hoc|||[Power View pour SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=391858)||||  
|Créer des tableaux de bord|||[Tableaux de bord SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=391859)<br /><br /> [Services PerformancePoint](https://technet.microsoft.com/library/ee424392.aspx)||||  
|Créer des rapports opérationnels||||||<sup>1</sup> [Reporting Services](create-deploy-and-manage-mobile-and-paginated-reports.md)|  
|Créer des rapports personnalisés et incorporés||||||<sup>1</sup> [Reporting Services](create-deploy-and-manage-mobile-and-paginated-reports.md)|  
|**Analytique avancée**|Scientifique des données||||||  
|Effectuer des analyses prédictives en libre-service||||||[Compléments d'exploration de données pour Excel](https://msdn.microsoft.com/library/dn282385\(v=sql.120\).aspx)|  
|Utiliser des algorithmes d'exploration de données||||||[Exploration de données dans Analysis Services](https://technet.microsoft.com/library/bb510516\(v=sql.120\).aspx)|  
  
 <sup>1</sup> Reporting Services a un certain nombre de fonctionnalités qui prennent en charge la transmission de rapports opérationnels et de rapports personnalisés, tels que les abonnements et les alertes de données.