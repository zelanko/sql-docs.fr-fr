---
title: Comparer les fonctionnalités de Business Intelligence dans différents environnements Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 1fb759ee-8172-4c4c-9f7d-49af2c731006
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8dcd0f49e59a95396e25f9504abc37e58e6ec4b7
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53374871"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>Comparer les fonctionnalités de Business Intelligence dans différents environnements Microsoft
  Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence peut être déployé dans plusieurs environnements différents, y compris [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec SharePoint Server, SharePoint Online et Power BI pour Office 365. Cette rubrique compare les composants et les fonctionnalités pris en charge dans chaque environnement.  
  
 Pour plus d'informations sur la comparaison de SharePoint Server avec SharePoint Online, consultez [Comparer les plans et les options de SharePoint](http://products.office.com/SharePoint/compare-sharepoint-plans).  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>Créer et gérer des rapports et des tableaux de bord BI  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online – Plan 2|Power BI pour Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Sites BI|Galerie [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]|Non|Sites Power BI|  
|Gestion des données, et partage et gestion des requêtes|Non|Non|Oui **<sup>1</sup>**|  
|Intégration avec Master Data Services (MDS) et Data Quality Services (DQS)|Oui|Non|Non|  
|Actualisation des données de planification|Oui, mais ne prend pas en charge des classeurs contenant des données Power Query|Non|Oui|  
|Requête en langage naturel (Q&R)|Non|Non|Oui **<sup>2</sup>**|  
|Prévision prédictive|Non|Non|Oui **<sup>3</sup>**|  
|Intégration de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Oui|Non|Non|  
|Intégration d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (multidimensionnel et tabulaire)|Oui|Non|Non|  
|Exporter un tableau de bord interactif Power View vers une présentation PowerPoint|Oui|Non|Non|  
|Création du tableau de bord dans un navigateur|Oui|Non|Non|  
|Surveillance de l'utilisation|Oui|Non|Oui|  
|Tirer parti de la sécurité de niveau ligne des cubes [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Oui|Non|Non|  
  
 **<sup>1</sup>**[compréhension du rôle des gestionnaires de données dans la gestion des données](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US) et [vidéo :   Gestion des informations de BI et gestion des données Power](https://www.youtube.com/watch?v=8dHOj68ts7c).  
  
 **<sup>2</sup>**[power BI Q & r :   Optimiser un classeur Power BI (modélisation cloud)](https://support.office.com/article/Power-BI-Q-A-Optimize-a-Power-BI-workbook-cloud-modeling--96dc5941-d0f1-44e2-9d9d-c038a3a55849?ui=en-US&rs=en-US&ad=US).  
  
 **<sup>3</sup>**  [Présentation des nouvelles capacités de prévision de Power View pour Office 365](https://blogs.msdn.com/b/powerbi/archive/2014/05/08/introducing-new-forecasting-capabilities-in-power-view-for-office-365.aspx).  
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>Afficher et parcourir les données, les rapports et les tableaux de bord BI  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online – Plan 2|Power BI pour Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Afficher les classeurs Microsoft Excel dans un navigateur|Oui, si la taille du classeur est inférieure à 2 Go|Oui, si la taille du classeur est inférieure à 10 Mo|Oui, si la taille du classeur est inférieure à 250 Mo|  
|Exploration de données dans un navigateur en HTML5|Non|Non|Oui|  
|Application mobile BI pour accéder à distance à des rapports et à des tableaux de bord|Non|Non|Oui **<sup>1</sup>**|  
|Classeur Excel avec [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] comme source de données **<sup>2</sup>**|Oui|Non|Non|  
|Possibilité d'utiliser les fonctionnalités dans différents navigateurs et versions|Oui, pour les visualisations non-Power View **<sup>3</sup>**|Oui, pour les fichiers de classeurs d'une taille inférieure à 10 Mo **<sup>3</sup>**|Oui **<sup>3</sup>**|  
  
 **<sup>1</sup>**  [Microsoft Power BI](http://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba).  
  
 **<sup>2</sup>**  [Classeurs PowerPivot comme source de données](http://blogs.technet.com/b/excel_services__powerpivot_for_sharepoint_support_blog/archive/2013/02/15/powerpivot-workbook-as-a-data-source.aspx)  
  
 **<sup>3</sup>**[prise en charge mobile sur les outils d’analyse décisionnelle (BI)](https://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx) et [planification pour Reporting Services et la prise en charge de navigateur Power View (Reporting Services 2014)](https://msdn.microsoft.com/library/ms156511.aspx).  
  
## <a name="more-information"></a>Informations complémentaires  
  
-   [Fonctionnalités de Business Intelligence dans Excel, SharePoint Online et Power BI pour Office 365](https://technet.microsoft.com/en-us/library/dn198235.aspx).  
  
-   Pour plus d'informations sur la configuration requise pour utiliser des synonymes, consultez [Ajouter des synonymes à un modèle de données Power Pivot Excel](https://support.office.com/Article/Add-synonyms-to-a-Power-Pivot-Excel-data-model-345f4f5b-5ec2-4998-bc46-a26bdc0810b6?ui=en-US&rs=en-US&ad=US).  
  
-   [Office Online, choisissez votre réseau social d’entreprise : Yammer ou Newsfeed ? ](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US).  
  
-   [Power BI pour Office 365](https://www.microsoft.com/powerbi/default.aspx).  
  
-   [Tarification de Power BI](https://www.microsoft.com/powerBI/pricing.aspx).  
  
-   [Comparer un site BI Center à des sites Power BI pour Office 365](https://technet.microsoft.com/library/dn394343\(v=office.15\).aspx).  
  
-   [Présentation des outils d’analyse et de création de rapports Microsoft BI](https://go.microsoft.com/fwlink/p/?LinkId=617093)  
  
## <a name="community-content"></a>Contenus de la Communauté  
 [BI en libre-service Microsoft en local et dans le cloud](http://businessintelligist.com/2014/02/07/microsoft-self-service-bi-on-premise-vs-could/).  
  
  
