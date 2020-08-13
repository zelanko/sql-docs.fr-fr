---
title: Fonctionnalités prises en charge par différentes éditions - SQL Server Reporting Services | Microsoft Docs
description: Découvrez les fonctionnalités SQL Server Reporting Services (SSRS) qui sont prises en charge par les différentes éditions de SQL Server.
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.date: 12/16/2019
ms.openlocfilehash: bbb3196349c648b955e5d27bf1d5fcfdadb9085f
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246658"
---
# <a name="sql-server-reporting-services-features-supported-by-editions"></a>Fonctionnalités SQL Server Reporting Services prises en charge par les éditions

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Cette rubrique explique les fonctionnalités SQL Server Reporting Services (SSRS) prises en charge par les différentes éditions de SQL Server. La version d’évaluation de SQL Server est disponible pendant une période d’évaluation de 180 jours.  

## <a name="related-links"></a>Liens connexes
  
 - [Notes de publication de SQL Server Reporting Services (SSRS)](release-notes-reporting-services.md). 
 - [Nouveautés de SQL Server Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).
 - [Fonctionnalités prises en charge par les éditions de SQL Server](~/sql-server/editions-and-components-of-sql-server-version-15.md)

##  <a name="sql-server-reporting-services"></a><a name="SSRS"></a> SQL Server Reporting Services  

Pour connaître les fonctionnalités prises en charge par les éditions Evaluation et Developer, consultez la colonne SQL Server Enterprise dans le tableau suivant.

|Nom de la fonctionnalité|Entreprise|Standard|Web|Express with Advanced Services|Développeur|  
|------|---------|---------------|-----------|-------|---------|  
| Rapports Power BI et classeurs Excel | Oui, avec Software Assurance | | | | Oui |
|Rapports mobiles et analyse|Oui||||Oui|  
|Édition [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prise en charge pour la base de données du catalogue|Standard ou supérieur|Standard ou supérieur|Web|Express|Standard ou supérieur|  
|Sources de données prises en charge par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Toutes les éditions   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Toutes les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Web|Express|Toutes les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|  
|Serveur de rapports|Oui|Oui|Oui|Oui|Oui|  
|Concepteur de rapports|Oui|Oui|Oui|Oui|Oui|  
|Portail web Concepteur de rapports|Oui|Oui|Oui|Oui|Oui|  
|Sécurité basée sur les rôles|Oui|Oui|Oui|Oui|Oui|  
|Exporter vers Excel, PowerPoint, Word, PDF et images|Oui|Oui|Oui|Oui|Oui|  
|Jauges et graphiques améliorés|Oui|Oui|Oui|Oui|Oui|  
|Épingler des éléments de rapport à des tableaux de bord [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]|Oui|Oui|Oui|Oui|Oui|  
|Authentification personnalisée|Oui|Oui|Oui||Oui|  
|Rapport en tant que flux de données|Oui|Oui|Oui|Oui|Oui|  
|Prise en charge des modèles|Oui|Oui|Oui||Oui|  
|Créer des rôles personnalisés pour la sécurité basée sur les rôles|Oui|Oui|||Oui|  
|Sécurité de l'élément de modèle|Oui|Oui|||Oui|  
|Rapport généré interactif infini|Oui|Oui|||Oui|  
|Bibliothèque de composants partagés|Oui|Oui|||Oui|  
|Abonnements et planifications par partage de fichiers et messagerie électronique|Oui|Oui|||Oui|  
|Historique de rapport, exécution d'instantanés et mise en cache|Oui|Oui|||Oui|  
|Intégration SharePoint<sup>2</sup>|Oui|Oui|||Oui|  
|Prise en charge de sources de données distantes et non-SQL<sup>1</sup>|Oui|Oui|||Oui|  
|Source de données, remise, rendu et extensibilité RDCE|Oui|Oui|||Oui|  
|Options de personnalisation|Oui||||Oui|  
|Abonnement à un rapport piloté par les données|Oui||||Oui|  
|Déploiement avec montée en puissance parallèle (batteries de serveurs Web)|Oui||||Oui|  
|Alerte<sup>2</sup> (SSRS 2016) |Oui||||Oui|  
|Power View<sup>2</sup> (SSRS 2016) |Oui||||Oui| 
|Commentaires<sup>3</sup> |Oui|Oui|Oui|Oui|Oui|  

 <sup>1</sup> Pour plus d’informations sur les sources de données prises en charge dans SQL Server Reporting Services (SSRS), consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
 <sup>2</sup> Exige SQL Server 2016 Reporting Services en mode SharePoint. Pour plus d’informations, consultez [Installer SQL Server Reporting Services en mode SharePoint](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md). À compter de SQL Server 2017 Reporting Services, l’intégration à SharePoint n’est plus disponible. 

<sup>3</sup> Uniquement dans Power BI Report Server et SQL Server 2017 Reporting Services (et versions ultérieures).

> [!NOTE]
> SQL Server Express Tools and SQL Server Express ne prennent pas en charge Reporting Services.
  
## <a name="edition-requirements-for-the-report-server-database"></a>Conditions requises pour l'édition de la base de données du serveur de rapports
 Lors de la création d'une base de données de serveur de rapports, toutes les éditions de SQL Server [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peuvent pas être utilisées pour héberger la base de données. Le tableau suivant répertorie les éditions du [!INCLUDE[ssDE](../includes/ssde-md.md)] que vous pouvez utiliser pour les éditions spécifiques de SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Pour cette édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services,|utilisez cette édition de l'instance du moteur de base de données pour héberger la base de données.|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Entreprise|Éditions Standard ou Enterprise (locales ou distantes)|  
|Standard|Éditions Standard ou Enterprise (locales ou distantes)|  
|Web|Web Edition (locale uniquement)|  
|Express with Advanced Services|Express with Advanced Services (local uniquement)|  
|Évaluation|Évaluation|  
  
##  <a name="business-intelligence-clients"></a><a name="BIC"></a> Clients Business Intelligence  
Les applications logicielles clientes suivantes sont disponibles dans le Centre de téléchargement Microsoft. Elles vous aident à créer des documents Business Intelligence qui s’exécutent sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Lorsque vous hébergez ces documents dans un environnement serveur, utilisez une édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui prend en charge ce type de document. Le tableau suivant identifie quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient les fonctionnalités de serveur obligatoires pour héberger les documents créés dans ces applications clientes.  
  
|Nom de l’outil|Entreprise|Standard|Web|Express with Advanced Services|Développeur|  
|---------------|----------------|--------------|------------------------|-------------|---------------| 
| Power BI Desktop optimisé pour le serveur de rapports Power BI, **.pbix** | Oui, avec Software Assurance | | | | Oui |
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)], **.rdl** et **.rds**|Oui|Oui|Oui|Oui|Oui|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)], **.rsmobile**|Oui||||Oui|  
|Applications Power BI pour appareils mobiles (iOS, Windows 10 et Android), **.rsmobile**|Oui||||Oui|  
  
> [!NOTE]  
> * Le tableau ci-dessus identifie les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nécessaires pour activer ces outils clients. Toutefois, ces outils peuvent accéder aux données hébergées de n’importe quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
> * [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] est le seul point de création de rapports mobiles. Connectez-vous à un serveur SSRS pour accéder aux sources de données et créer des rapports. Ensuite, publiez-les sur le serveur SSRS pour que d’autres utilisateurs de l’organisation puissent y accéder, soit sur le serveur, soit sur des appareils mobiles. Vous pouvez également utiliser le [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] autonome avec des sources de données locales.  
> * Si vous utilisez [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] localement, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] dans le cloud ou les deux pour votre solution de remise de rapports, vous avez besoin d’une seule application mobile pour accéder aux tableaux de bord et aux rapports mobiles sur des appareils mobiles. Les applications [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] sont disponibles au téléchargement à partir des App Store Windows, iOS et Android.  

## <a name="next-steps"></a>Étapes suivantes

* En savoir plus sur les [fonctionnalités prises en charge par les éditions de SQL Server 2017](~/sql-server/editions-and-components-of-sql-server-2017.md). 

* [Planifier une installation de SQL Server](../sql-server/install/planning-a-sql-server-installation.md).

* D’autres questions ? Posez-les sur le [forum SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
