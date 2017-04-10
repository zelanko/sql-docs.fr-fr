---
title: "Technical Preview of Power BI reports in SSRS - Release notes (Version d’&#233;valuation technique des rapports Power Bi dans SSRS - Notes de publication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f20d7-a9f9-47e3-8dc3-c544a14457e0
caps.latest.revision: 5
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Notes de publication sur Reporting Services
 ||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]** Version d’évaluation technique de janvier 2017 des rapports Power BI de SQL Server Reporting Services|

Cette rubrique décrit les limites et problèmes liés à la version d’évaluation technique des rapports Power BI de SQL Server Reporting Services.

- Pour connaître les nouveautés de cette version, consultez l’article [Nouveautés de Reporting Services](../reporting-services/nouveautés-de-sql-server-reporting-services-ssrs.md).

 **Essayez-le :**    
   -   [![Téléchargement à partir du Centre de téléchargement Microsoft](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?linkid=839351) Télécharger la version d’évaluation technique des rapports Power BI de SQL Server Reporting Services et Power BI Desktop (SQL Server Reporting Services) à partir du **[Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=839351)**


## <a name="january--2017"></a>Janvier 2017

### <a name="report-server"></a>Serveur de rapports

- Le protocole HTTPS est désormais pris en charge. Il n’était pas disponible dans la version Technical Preview VM publiée en octobre 2016. Pour plus d’informations, consultez [Configurer des connexions SSL sur un serveur de rapports en mode natif](../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).
   - Le protocole HTTPS est requis pour utiliser le complément Visionneuse web de PowerPoint et y afficher les rapports Power BI.
- L’augmentation de la taille des instances est désormais prise en charge. Elle n’était pas disponible dans la version Technical Preview VM publiée en octobre 2016. Pour plus d’informations, consultez l’article [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif](../reporting-services/install-windows/configure a native mode report server scale-out deployment.md).

### <a name="power-bi-reports"></a>Rapports Power BI

- Les rapports Power BI doivent être créés avec Power BI Desktop (SQL Server Reporting Services) afin de fonctionner avec SQL Server Reporting Services. Vous pouvez télécharger Power BI Desktop (SQL Server Reporting services) à partir du Centre d’évaluation.
- Les rapports Power BI ne prennent en charge que les connexions actives à Analysis Services (tabulaires ou multidimensionnels).
- Pas de prise en charge des éléments visuels personnalisés.
- Pas de prise en charge des éléments visuels R.