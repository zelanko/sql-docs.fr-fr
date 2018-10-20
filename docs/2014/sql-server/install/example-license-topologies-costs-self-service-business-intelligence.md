---
title: Exemples de Topologies de licence et coûts pour SQL Server 2014 Self-service Business Intelligence | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 682b8711-407a-48d1-9807-415d4c24dad6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a7e08f483f1f56dcab49391190fd1c6edc11f6db
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49462055"
---
# <a name="example-license-topologies-and-costs--for-sql-server-2014-self-service-business-intelligence"></a>Exemple de topologies et coûts des licences pour SQL Server 2014 Self-Service Business Intelligence
  Cette rubrique illustre les points importants dont vous devez tenir compte lorsque vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Business Intelligence ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise. Elle contient plusieurs exemples de topologies Business Intelligence (BI) libre-service Microsoft sur site. Les exemples incluent les éditions et les licences que vous pouvez utiliser pour optimiser l'équilibre entre le coût et les performances. Les topologies, le nombre de serveurs et le coût de licence sont fournis **uniquement comme exemples**. Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et Microsoft SharePoint 2013 ont introduit plusieurs modifications des modèles de licence qui fournissent des options supplémentaires pour concéder sous licence vos serveurs, utilisateurs et périphériques. La licence [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge les mêmes scénarios liés à Business Intelligence.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est disponible dans l'édition Business Intelligence et propose une licence par cœur pour certaines éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   SharePoint 2013 simplifie le modèle de licence SharePoint Server pour les scénarios extranet et intranet, ainsi que les options pour SharePoint Online.  
  
 Avant l'achat, consultez la section « Comment acheter » de chaque produit et votre représentant ou revendeur local Microsoft, en ce qui concerne vos exigences en matière de licence. Pour plus d'informations sur les derniers plans et coûts de gestion des licences, consultez les rubriques suivantes :  
  
-   [À propos des licences-SQL Server 2014](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx)  
  
-   [Licences SharePoint 2013](http://office.microsoft.com/sharepoint/sharepoint-licensing-overview-collaboration-software-FX103789438.aspx).  
  
 **Dans cette rubrique :**  
  
-   [Composants de SQL Server Business Intelligence](#bkmk_bi_components)  
  
-   [Résumé des licences SQL Server 2014](#bkmk_sql_server_license)  
  
-   [Résumé des licences SharePoint 2013](#bkmk_sharepoint_license)  
  
-   [Topologie à 3 niveaux avec des serveurs distincts PowerPivot](#bkmk_3tier_powerpivot)  
  
-   [Topologie à 3 niveaux](#bkmk_3tier)  
  
-   [Topologie à 2 niveaux](#bkmk_2tier)  
  
-   [Contenu de référence et de la Communauté](#bkmk_reference)  
  
##  <a name="bkmk_bi_components"></a> Composants de SQL Server Business Intelligence  
 Cette rubrique traite des technologies serveur SQL Server et SharePoint. Les coûts et les exemples n'illustrent pas spécifiquement les composants Microsoft Windows Server ou Microsoft Office dont vous avez besoin pour une solution client et serveur complète. Les composants SQL Server Business Intelligence traités dans cette rubrique sont SQL Server Reporting Services exécuté en mode SharePoint et PowerPivot pour SharePoint. Les composants incluent les fonctionnalités suivantes :  
  
-   Classeurs PowerPivot interactifs dans le navigateur.  
  
-   Rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] interactifs dans SharePoint.  
  
-   Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], Planifier l'actualisation des données, Tableau de bord de gestion.  
  
-   Reporting Services en mode SharePoint, y compris Alertes de données.  
  
 Pour plus d’informations, consultez le tableau des fonctionnalités de [installer des fonctionnalités SQL Server BI avec SharePoint &#40;PowerPivot et Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="license-summary"></a>Résumé des licences  
 Cette section résume les conditions de licence pour SQL Server et SharePoint. Les informations sont une synthèse de haut niveau et couvrent uniquement les scénarios utilisés dans les exemples de schémas de topologie et de coût de ce document. Pour plus d'informations sur les licences, consultez les liens indiqués. Les exemples de prix reposent sur les prix MOLP (Microsoft Open License Program).  
  
 Une pratique courante consiste à utiliser **Enterprise Edition** pour les serveurs qui exécutent le moteur de base de données SQL Server et **Business Intelligence Edition** pour les serveurs qui exécutent Reporting Services ou PowerPivot pour SharePoint. Toutefois, le **nombre d'utilisateurs** et le **nombre de cœurs des serveurs** dans votre déploiement affectent le coût et votre décision concernant l'édition à utiliser.  
  
###  <a name="bkmk_sql_server_license"></a> Résumé des licences SQL Server 2014  
  
-   SQL Server Entreprise Edition utilise les licences par cœur. Les licences par cœur sont vendues par packs de **deux cœurs** .  
  
-   L'édition SQL Server BI utilise des licences Serveur et des licences d'accès client (CAL).  
  
-   Les CAL sont basées sur chaque utilisateur ou périphérique connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quel que soit le nombre de serveurs auquel il se connecte.  
  
-   Les licences par cœur exigent que tous les cœurs du serveur soient couverts par une licence. Il existe un minimum de **quatre** licences par cœur pour chaque processeur physique du serveur.  
  
 Le tableau suivant récapitule les informations sur les licences utilisées pour le déploiement et l'estimation du coût des licences. **REMARQUE :**  le tarif est indiqué à titre de démonstration uniquement.  
  
|Éditions de SQL Server|Licence SQL Server + licence d'accès client (CAL)|Licence par cœur SQL Server|  
|-------------------------|---------------------------------------------------------|-----------------------------------|  
|Enterprise|Non applicable|**(Oui)** $6874 X [nb de cœurs] X [facteur de cœur]|  
|Business Intelligence|**(Oui)** $8592 + $199 par licence d'accès client|Non applicable|  
|Standard|**(Oui)**|**(Oui)**|  
  
 Pour plus d'informations sur l'exemple de tarif pour les licences [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez :  
  
-   [Gestion des licences pour les environnements virtuels](http://www.microsoft.com/licensing/about-licensing/virtualization.aspx) (http://www.microsoft.com/licensing/about-licensing/virtualization.aspx).  
  
-   [Fiche de gestion des licences de SQL Server 2014 - Page d’accueil Microsoft](http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) (http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [Éditions de SQL server 2014 et les licences](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx#tab=2)  
  
1.  **Hypothèses pour SQL Server et autres informations de licences :**  
  
2.  Les diagrammes de cette rubrique utilisent SQL Server Enterprise Edition pour les serveurs de base de données afin que l'ensemble complet de fonctionnalités à haute disponibilité soit disponible, par exemple, les groupes de disponibilité AlwaysOn. Pour plus d'informations, consultez [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
3.  Les serveurs dans cet exemple sont tous dotés de 2 processeurs 6 cœurs Intel Xeon. Par conséquent, il existe un **facteur de cœur SQL Server** de **1** lors du calcul du coût de la licence. Pour plus d’informations sur les facteurs de cœur et les coûts de licence, consultez [Table de facteur de SQL Server Core](http://download.microsoft.com/download/9/B/F/9BF63163-D8F9-4339-90AA-EBC9AAFC49AD/SQL2012_CoreFactorTable_Mar2012.pdf) (http://download.microsoft.com/download/0/C/8/0C85665B-11EA-4FF5-B37C-8CC21CF95AC4/BizTalk%202013_CoreFactorTable_**3.19.2013**. v4.pdf).  
  
###  <a name="bkmk_sharepoint_license"></a> Résumé des licences SharePoint 2013  
 La liste suivante récapitule le modèle de licence utilisé pour le déploiement et l'estimation du coût des licences. le tarif est indiqué à titre de démonstration uniquement.  
  
1.  Une licence serveur SharePoint est requise pour chaque instance de Microsoft SharePoint Server.  
  
2.  Pour concéder sous licence SharePoint Enterprise, pour chaque utilisateur final ou périphérique, procurez-vous une **Licence d'Accès Client Standard** Microsoft SharePoint Server 2013 en plus d'une **Licence d'Accès Client Enterprise**Microsoft SharePoint Server 2013.  
  
3.  Les CAL SharePoint sont achetées par utilisateur ou par périphérique qui ont accès aux serveurs SharePoint. Vous n'avez pas besoin d'acquérir des CAL pour chaque serveur.  
  
 Par exemple, votre environnement se compose de 2 instances utilisées par 100 utilisateurs, et vos coûts sont indiqués entre guillemets, où :  
  
-   Licence CAL Standard Microsoft SharePoint Server 2013 : **$107.99**  
  
-   Licence CAL Enterprise Microsoft SharePoint Server 2013 : **$94.99**  
  
-   Licence Microsoft SharePoint Server 2013 : **$6,412.99**  
  
 Le coût est de : **$33.123,98**  
  
-   CAL : ($107.99 +$94.99) X 100) =$20,298.00  
  
-   Licence Serveur : ($6,412.99 X 2) =$12,825.98  
  
 **Hypothèses pour SharePoint et autres informations de licences :**  
  
 Les exemples de déploiement sont tous les environnements intranet, par conséquent des CAL SharePoint sont nécessaires.  
  
-   [La liste complète des licences SharePoint](http://technet.microsoft.com/library/jj819267.aspx#bkmk_FeaturesOnPremise) (http://technet.microsoft.com/library/jj819267.aspx#bkmk_FeaturesOnPremise).  
  
-   [Comment acheter SharePoint](http://sharepoint.microsoft.com/Pages/buy.aspx) (http://sharepoint.microsoft.com/Pages/buy.aspx).  
  
##  <a name="bkmk_3tier_powerpivot"></a> Topologie avec différentes à 3 couches [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] serveurs  
 Cet exemple illustre qu'avec au plus 800 utilisateurs, il est moins onéreux d'utiliser SQL Server BI pour les serveurs d'applications SharePoint et les serveurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint. Toutefois, lorsqu'il y a 800 utilisateurs ou plus, SQL Server Entreprise Edition est moins onéreux. Les licences par cœur sont indépendantes du nombre d'utilisateurs, et par conséquent il existe un point de seuil de coût lorsque vous comparez le coût des CAL et des licences par cœur et que le nombre d'utilisateurs augmente. À partir du point de seuil, la solution la moins onéreuse est Enterprise Edition. Pour déterminer le seuil de coût, comparez le coût en fonction du nombre de cœurs à concéder sous licence et du nombre de CAL d'utilisateur final ou de périphérique à concéder sous licence.  
  
-   Voici un exemple de déploiement intranet ; par conséquent, des CAL SharePoint s'appliquent pour SharePoint 2013.  
  
-   Le rôle d'application (2) inclut SQL Server Reporting Services installé en mode SharePoint.  
  
     Les bases de données d'application de service SharePoint s'exécutent sur des serveurs (4) de rôle de base de données.  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint s'exécute sur des serveurs distincts (3). [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint 2013 s’exécute en dehors de la batterie de serveurs SharePoint et peut être installé sur les serveurs qui n’incluent pas d’une installation de SharePoint, amélioration des performances.  
  
-   Le rôle de base de données (4) utilise SQL Server Entreprise afin que la fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Groupes de disponibilité AlwaysOn, soit disponible.  
  
 ![bi_license_3tiers_and_ASseparate](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseparate.gif "bi_license_3tiers_and_ASseparate")  
  
 Avec 100 utilisateurs, l'édition SQL Server BI est la moins coûteuse.  
  
 ![bi_license_3tiers_and_ASseperate_calcs](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs.gif "bi_license_3tiers_and_ASseperate_calcs")  
  
 Toutefois, lorsqu'il y a 300 utilisateurs, l'utilisation de SQL Server Entreprise Edition est moins onéreuse.  
  
 ![bi_license_3tiers_and_ASseperate_calcs2](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs2.gif "bi_license_3tiers_and_ASseperate_calcs2")  
  
##  <a name="bkmk_3tier"></a> Topologie à 3 niveaux  
 Cet exemple montre qu'avec au plus 100 utilisateurs, il est moins onéreux d'utiliser SQL Server BI pour les serveurs qui exécutent les fonctionnalités SQL Server BI. Toutefois, lorsqu'il y a 500 utilisateurs ou plus, SQL Server Entreprise Edition est moins onéreux.  
  
-   Voici un exemple de déploiement intranet ; par conséquent, des CAL SharePoint s'appliquent pour SharePoint 2013.  
  
-   Analysis Services en mode PowerPivot (2) s'exécute à l'extérieur de la batterie mais PowerPivot s'exécute **sur les mêmes serveurs physiques** dans l'autre rôle d'application.  
  
-   Le rôle de base de données (3) utilise SQL Server Entreprise afin que la fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Groupes de disponibilité AlwaysOn, soit disponible.  
  
 ![bi_license_3tiers](../../../2014/sql-server/install/media/bi-license-3tiers.gif "bi_license_3tiers")  
  
 Avec 100 utilisateurs, l'édition SQL Server BI est la moins coûteuse.  
  
 ![bi_license_3tiers_calcs1](../../../2014/sql-server/install/media/bi-license-3tiers-calcs1.gif "bi_license_3tiers_calcs1")  
  
 Toutefois, lorsqu'il y a 500 utilisateurs, l'utilisation de SQL Server Entreprise Edition est moins onéreuse.  
  
 ![bi_license_3tiers_calcs3](../../../2014/sql-server/install/media/bi-license-3tiers-calcs3.gif "bi_license_3tiers_calcs3")  
  
##  <a name="bkmk_2tier"></a> Topologie à 2 niveaux  
 Avec uniquement 2 niveaux, SQL Server Entreprise Edition est utilisé afin que la fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Groupes de disponibilité AlwaysOn, soit disponible pour le moteur de base de données SQL Server. Par conséquent, il n'y a pas de différences de coût pour effectuer une comparaison entre les éditions de SQL Server. La seule variable est le prix des CAL SharePoint en fonction du nombre d'utilisateurs.  
  
-   Voici un exemple de déploiement intranet ; par conséquent, des CAL SharePoint s'appliquent pour SharePoint 2013.  
  
-   Analysis Services en mode PowerPivot s'exécute à l'extérieur de la batterie mais PowerPivot s'exécute sur les mêmes serveurs physiques (2) dans le moteur de base de données SQL Server.  
  
 ![bi_license_2tiers](../../../2014/sql-server/install/media/bi-license-2tiers.gif "bi_license_2tiers")  
  
 ![bi_license_2tiers_calcs1](../../../2014/sql-server/install/media/bi-license-2tiers-calcs1.gif "bi_license_2tiers_calcs1")  
  
##  <a name="bkmk_reference"></a> Contenu de référence et de la Communauté  
  
### <a name="license-tools"></a>Outils de gestion des licences  
  
-   [Microsoft License Advisor](http://mla.microsoft.com/default.aspx) (http://mla.microsoft.com/default.aspx).  
  
-   [Licences d’accès client (CAL) outil](http://www.microsoft.com/licensing/CalTool/) (http://www.microsoft.com/licensing/CalTool/).  
  
-   [Hub d’entreprise Microsoft : Comment acheter](http://www.microsoftbusinesshub.com/How_To_Buy#) (http://www.microsoftbusinesshub.com/How_To_Buy#).  
  
### <a name="microsoft-license-information"></a>Informations sur les licences Microsoft  
  
-   [Licences sur : Licences d’accès Client et licences de gestion](http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx) (http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx).  
  
-   [Propos des licences : Recherche des licences de produit](http://www.microsoftvolumelicensing.com/default.aspx) (http://www.microsoftvolumelicensing.com/default.aspx).  
  
-   [Licences en volume : tarification et comment acheter](http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx) (http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx).  
  
### <a name="community-content"></a>Contenus de la Communauté  
  
-   [Licences pour SQL Server 2014 Developer Edition](http://sqlmag.com/sql-server-2014/sql-server-2014-developer-edition-licensing).  
  
-   [Modifications des licences SQL Server 2014](http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes)(http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes).  
  
-   [Modification des licences pour SQL Server 2014](https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf)(https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf).  
  
-   [Estimation des coûts de licence de SharePoint 2013](http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/) (http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/).  
  
-   [Communauté de clients de licences en Volume Microsoft](http://www.microsoft.com/licensing/existing-customers/community.aspx) (http://www.microsoft.com/licensing/existing-customers/community.aspx).  
  
  
