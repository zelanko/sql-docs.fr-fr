---
title: "Reporting Services (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "rapports [Reporting Services]"
  - "SSRS"
  - "rapports [Reporting Services], à propos des rapports"
  - "Reporting Services"
  - "SQL Server Reporting Services"
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
caps.latest.revision: 70
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Reporting Services (SSRS)
  Créer, déployer et gérer localement des rapports paginés et mobiles grâce aux outils et services prêts à l’emploi fournis par SQL Server Reporting Services (SSRS). 
  
 ![SQL Server Reporting Services all together](../reporting-services/media/ss-reporting-services-all-together.png "SQL Server Reporting Services all together")  
## <a name="what-is-sql-server-reporting-services-ssrs"></a>Qu’est-ce que SQL Server Reporting Services (SSRS) ?

SQL Server Reporting Services est une solution que les clients déploient localement pour créer, publier et gérer des rapports, puis les remettre aux utilisateurs appropriés de différentes façons, que ce soit dans un navigateur web, sur leurs appareils mobiles ou dans un e-mail.

Pour SQL Server 2016, Reporting Services offre une suite de produits mise à jour :

* **Rapports paginés « traditionnels »** mis à jour, pour vous permettre de créer des rapports modernisés, avec des outils mis à jour et de nouvelles fonctionnalités pour les créer. 
* **Nouveaux rapports mobiles** avec une disposition réactive qui s’adapte aux différents appareils et aux différentes façons de les tenir en main. 
* **Portail web moderne** que vous pouvez afficher dans n’importe quel navigateur moderne. Dans le nouveau portail, vous pouvez organiser et afficher des rapports paginés et mobiles, ainsi que de nouveaux indicateurs de performance clés. Vous pouvez également stocker des classeurs Excel et des rapports Power BI Desktop sur le portail. 

Pour en savoir plus, lisez la suite de cet article.
  
### <a name="whats-new-in-reporting-services"></a>Nouveautés de Reporting Services

Ces sources vous permettent de rester informé des nouvelles fonctionnalités de SQL Server 2016 Reporting Services. 
* [Nouveautés de Reporting Services](../reporting-services/nouveautés-de-sql-server-reporting-services-ssrs.md)
* [Blog de l’équipe SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Canal YouTube Guy in a Cube](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)
  
## <a name="paginated-reports"></a>Rapports paginés

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

Reporting Services est associé à des rapports paginés « traditionnels » de style document, dans lesquels plus vous avez de données, plus il y a de lignes dans les tables et plus le rapport a de pages. Ceci est idéal pour générer des documents à disposition fixe, parfaitement optimisés pour l’impression, tels que les fichiers PDF et Word. 

Cette charge de travail BI principale existe toujours aujourd’hui, donc nous l’avons modernisée. Vous pouvez désormais créer des rapports modernisés grâce aux fonctionnalités nouvelles et mises à jour, à l’aide du [Générateur de rapports](../reporting-services/report-builder/report-builder-in-sql-server-2016.md) ou du [Concepteur de rapports dans SQL Server Data Tools (SSDT)](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md). 

* Nous avons mis à jour tous les styles et palettes de couleurs par défaut. Ainsi, par défaut vous créez des rapports avec un nouveau style moderne minimaliste.
* Nous avons mis à jour le volet Paramètres pour que vous puissiez réorganiser les paramètres comme vous le souhaitez.
* Vous pouvez exporter dans de nouveaux formats tels que PowerPoint. Les visualisations Reporting Services dans PowerPoint sont dynamiques et modifiables ; il ne s’agit pas simplement de captures d’écran.
* Vous pouvez créer une expérience hybride Power BI/Reporting Services : plutôt que de recréer vos rapports Reporting Services locaux dans Power BI, vous pouvez épingler des visuels à partir de ces rapports dans vos tableaux de bord Power BI. Ensuite, vous pouvez surveiller tous les éléments dans un emplacement unique sur votre tableau de bord.
 
## <a name="mobile-reports"></a>Rapports mobiles

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

Avec le succès de l’informatique mobile, les utilisateurs ont aujourd’hui des besoins différents en matière de création de rapports. L’affichage des rapports à la disposition fixe ne convient pas vraiment quand il s’agit de tablettes et de téléphones. Quelque chose conçu pour un grand écran de PC ne constitue pas une expérience optimale sur un petit écran de téléphone, qui est non seulement plus petit, mais peut aussi avoir une orientation portrait ou paysage.

Ce dont vous avez besoin avec ces facteurs de forme d’écran très différents n’est pas une disposition fixe, mais une disposition réactive qui s’adapte à ces différents appareils et aux différentes manières dont vous les tenez en main. Pour cela, nous avons ajouté un nouveau type de rapport, les rapports mobiles, basés sur la technologie Datazen dont nous avons fait l’acquisition il y a environ un an et que nous avons intégrée au produit. Vous pouvez migrer vos rapports Datazen existants vers Reporting Services avec [l’Assistant Migration SQL Server pour Datazen](https://www.microsoft.com/download/details.aspx?id=53128). 

Vous créez ces rapports mobiles dans la nouvelle application [Éditeur de rapports mobiles](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md). Ensuite, dans les [applications Power BI pour appareils mobiles](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/) natives pour Windows 10, iOS, Android et HTML5, vous pouvez accéder aux données que vous avez dans Power BI dans le cloud, ainsi qu’à vos données SQL Server 2016 Reporting Services locales. À mesure que vous créez des visualisations, l’Éditeur de rapports mobiles génère automatiquement des exemples de données pour chacune d’elles. Vous voyez ainsi à quoi ressemblera la visualisation avec vos données et pouvez déterminer le type de données adapté à chaque visualisation.

## <a name="web-portal"></a>Portail web

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

Pour les utilisateurs finaux de Reporting Services en mode natif, la porte d’entrée est un portail web moderne que vous pouvez afficher dans n’importe quel navigateur moderne. Vous pouvez accéder à tous ces rapports paginés et mobiles, ainsi qu’aux nouveaux indicateurs de performance clés, dans le nouveau portail. Vous pouvez baliser vos favoris et gérer le contenu si vous avez ce rôle. 

Vous pouvez appliquer une personnalisation à votre portail web. Et vous pouvez créer des indicateurs de performance clés directement dans le portail web. Les indicateurs de performance clés peuvent exposer des métriques métier clés en un clin d’œil dans le navigateur, sans qu’il soit nécessaire d’ouvrir un rapport. 

Le nouveau portail web est une réécriture complète du Gestionnaire de rapports. Désormais, il s’agit d’une application HTML5 d’une seule page, basée sur des normes, pour laquelle les navigateurs modernes sont optimisés (Edge, Internet Explorer 10 et 11, Chrome, Firefox, Safari et tous les navigateurs les plus courants).

Le portail web propose toujours la hiérarchie de dossiers classique, qui vous permet d’organiser le contenu. Le contenu est organisé par type : rapports mobiles, indicateurs de performance clés, rapports paginés, ainsi que les rapports Power BI Desktop, les classeurs Excel, les datasets partagés et les sources de données partagées à utiliser comme composantes pour vos rapports. Vous pouvez les stocker et les gérer ici, en toute sécurité.

Et vous pouvez toujours planifier le traitement des rapports, accéder aux rapports à la demande et vous abonner à des rapports publiés dans le nouveau portail web.

Informations complémentaires sur le [portail web de Reporting Services](../reporting-services/web-portal-ssrs-native-mode.md).
  
## <a name="reporting-services-in-sharepoint-integrated-mode"></a>Reporting Services en mode intégré SharePoint  

Vous publiez des rapports dans Reporting Services en mode intégré SharePoint. Vous pouvez planifier le traitement des rapports, accéder aux rapports à la demande, vous abonner aux rapports publiés et exporter des rapports vers d’autres applications comme Microsoft Excel. Créez des alertes sur des rapports publiés sur un site SharePoint et recevez des messages électroniques lorsque les données du rapport sont modifiées.  

Informations complémentaires sur [Reporting Services Report Server en mode intégré SharePoint](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md).
 
## <a name="includessrsnoversiontokenssrsnoversionmdmd-programming-features"></a>Fonctionnalités de programmation de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
 Utilisez les fonctionnalités de programmation de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour étendre et personnaliser votre fonctionnalité de création de rapports, grâce aux API permettant d’intégrer et d’étendre le traitement des données et des rapports dans des applications personnalisées.
 
 Plus de [Documentation du développeur Reporting Services](../reporting-services/reporting-services-developer-documentation.md). 
  
## <a name="browse-content-by-area"></a>Parcourir le contenu par domaine  
* [Compatibilité descendante](../reporting-services/compatibilité-descendante-reporting-services.md) 
* [Serveur de rapports Reporting Services](../reporting-services/report-server-sharepoint/serveur-de-rapports-reporting-services.md)  
* [Le portail web](../reporting-services/web-portal-ssrs-native-mode.md)
* [Rapports Reporting Services &#40;SSRS&#41;](../reporting-services/reports/reporting-services-reports-ssrs.md)  
* [Données des rapports &#40;SSRS&#41;](../reporting-services/report-data/report-data-ssrs.md)  
* [Générateur de rapports dans SQL Server 2016](../reporting-services/report-builder/report-builder-in-sql-server-2016.md)  
* [Éditeur de rapports mobiles SQL Server](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
* [Indicateurs de performance clés (KPI) dans Reporting Services](../reporting-services/working-with-kpis-in-reporting-services.md)
* [Outils de Reporting Services](../reporting-services/tools/reporting-services-tools.md)  
  
## <a name="see-also"></a>Voir aussi  
* [Installer Reporting Services](../reporting-services/install-windows/install-reporting-services.md)
* [Installer le Générateur de rapports](../reporting-services/install-windows/install-report-builder.md)   
* [Télécharger SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)
  
  