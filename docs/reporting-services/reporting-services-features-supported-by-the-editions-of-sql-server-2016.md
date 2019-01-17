---
title: Fonctionnalités Reporting Services prises en charge par les éditions de SQL Server
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.date: 11/01/2018
ms.openlocfilehash: 37dec44c539db86f8f0d239fffe0ca28699f2799
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645328"
---
# <a name="reporting-services-features-supported-by-the-editions-of-sql-server"></a>Fonctionnalités Reporting Services prises en charge par les éditions de SQL Server

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)])

Cette rubrique fournit des détails sur les fonctionnalités prises en charge par les différentes éditions de SQL Server. La version d’évaluation de SQL Server est disponible pendant une période d’évaluation de 180 jours.  
  
 Pour obtenir les dernières notes de publication de SQL Server, consultez [Notes de publication de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md). Pour plus d’informations sur les nouveautés, consultez [Nouveautés de Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

 **Essayer SQL Server 2017**    

> [![Télécharger SQL Server 2017](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?LinkID=829477) **[Télécharger SQL Server 2017 à partir du Centre d’évaluation](https://go.microsoft.com/fwlink/?LinkID=829477)**    
>
> ![Petite machine virtuelle Azure](../analysis-services/media/azure-virtual-machine-small.png) **[Étendez une machine virtuelle sur laquelle SQL Server 2017 est déjà installé](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    

Pour connaître les fonctionnalités prises en charge par les éditions Evaluation et Developer, consultez la colonne Enterprise.

##  <a name="SSRS"></a> Reporting Services  
  
|Nom de la fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Développeur|  
|------------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Rapports mobiles et indicateurs de performance clés|Oui||||Oui|  
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
|Intégration SharePoint|Oui|Oui|||Oui|  
|Prise en charge de sources de données distantes et non-SQL<sup>1</sup>|Oui|Oui|||Oui|  
|Source de données, remise et rendu, extensibilité RDCE|Oui|Oui|||Oui|  
|Options de personnalisation|Oui||||Oui|  
|Abonnement aux rapports pilotés par les données|Oui||||Oui|  
|Déploiement avec montée en puissance parallèle (batteries de serveurs Web)|Oui||||Oui|  
|Alerte<sup>2</sup> (SSRS 2016) |Oui||||Oui|  
| Power View<sup>2</sup> (SSRS 2016) |Oui||||Oui| 
|Commentaires<sup>3</sup> |Oui|Oui|Oui|Oui|Oui|  

 <sup>1</sup> Pour plus d’informations sur les sources de données prises en charge dans SQL Server Reporting Services (SSRS), consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
 <sup>2</sup> Exige Reporting Services 2016 en mode SharePoint. Pour plus d’informations, consultez [Installer le mode SharePoint de Reporting Services](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md). À compter de Reporting Services 2017, l’intégration de Reporting Services à SharePoint n’est plus disponible. 

<sup>3</sup> Uniquement dans Power BI Report Server et Reporting Services 2017 (et versions ultérieures).

> [!NOTE]
> SQL Server Express Tools and SQL Server Express ne prennent pas en charge Reporting Services.
  
## <a name="report-server-database-server-edition-requirements"></a>Conditions requises pour l'édition SQL Server de la base de données du serveur de rapports
 Lors de la création d'une base de données de serveur de rapports, toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peuvent pas être utilisées pour héberger la base de données. Le tableau suivant répertorie les éditions du [!INCLUDE[ssDE](../includes/ssde-md.md)] que vous pouvez utiliser pour les éditions spécifiques de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Pour cette édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Utilisez cette édition de l'instance du moteur de base de données pour héberger la base de données|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Éditions Standard ou Enterprise (locales ou distantes)|  
|Standard|Éditions Standard ou Enterprise (locales ou distantes)|  
|Web|Web Edition (locale uniquement)|  
|Express with Advanced Services|Express with Advanced Services (local uniquement).|  
|Evaluation|Evaluation|  
  
##  <a name="BIC"></a> Clients Business Intelligence  
 Les applications logicielles clientes suivantes sont disponibles dans le Centre de téléchargement Microsoft ; elles ont pour but de vous aider à créer des documents décisionnels qui s’exécutent sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Lorsque vous hébergez ces documents dans un environnement serveur, utilisez une édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui prend en charge ce type de document. Le tableau suivant identifie quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient les fonctionnalités de serveur obligatoires pour héberger les documents créés dans ces applications clientes.  
  
|Nom de l’outil|Enterprise|Standard|Web|Express with Advanced Services|Développeur|  
|---------------|----------------|--------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)] (.rdl et .rds)|Oui|Oui|Oui|Oui|Oui|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] (.rsmobile)|Oui||||Oui|  
|Applications Power BI pour appareils mobiles (iOS, Windows 10, Android) (.rsmobile)|Oui||||Oui|  
  
> [!NOTE]  
> 1. Le tableau ci-dessus identifie les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requises pour activer ces outils clients ; toutefois, ces outils peuvent accéder aux données hébergées sur n’importe quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
> 2. [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] est le seul point de création de rapports mobiles. Connectez-vous à un serveur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour accéder aux sources de données et créer des rapports. Ensuite, publiez-les sur le serveur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour que d’autres utilisateurs de l’organisation puissent y accéder, soit sur le serveur, soit sur des appareils mobiles. Vous pouvez également utiliser le [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] autonome avec des sources de données locales.  
> 3. Si vous utilisez  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] localement, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] dans le cloud ou les deux pour votre solution de remise de rapports, vous avez besoin d’une seule application mobile pour accéder aux tableaux de bord et aux rapports mobiles sur des appareils mobiles. Les applications [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] sont disponibles au téléchargement à partir des App Store Windows, iOS et Android.  

## <a name="next-steps"></a>Étapes suivantes

[Fonctionnalités prises en charge par les éditions de SQL Server 2017](~/sql-server/editions-and-components-of-sql-server-2017.md)  
[Planifier une installation de SQL Server](../sql-server/install/planning-a-sql-server-installation.md) 

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
