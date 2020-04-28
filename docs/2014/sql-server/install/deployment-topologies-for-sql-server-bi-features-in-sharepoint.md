---
title: Topologies de déploiement pour les fonctionnalités de SQL Server BI dans SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 2ba357fc3910779573ffa36f3070b55c08ced8ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388724"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>Topologies de déploiement pour les fonctionnalités SQL Server BI dans SharePoint
  Cette rubrique décrit les topologies courantes pour l'installation des fonctionnalités SQL Server Business Intelligence de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] dans les environnements SharePoint 2010 et SharePoint 2013. Par exemple, des installations à trois niveaux et de serveur unique.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **Dans cette rubrique :**  
  
-   [Exemples de topologies de déploiement de SharePoint 2013](#bkmk_example_deployments_2013)  
  
    -   [Déploiement à trois serveurs de PowerPivot pour SharePoint 2013 et Reporting Services](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [Déploiement mono-serveur de PowerPivot pour SharePoint 2013](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [Déploiement à deux serveurs de PowerPivot pour SharePoint 2013](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [Déploiement à trois serveurs de PowerPivot pour SharePoint 2013](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [Déploiement à un seul serveur de PowerPivot pour SharePoint 2013 et Reporting Services](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [Déploiement à deux serveurs de PowerPivot pour SharePoint 2013 et Reporting Services](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [Exemples de topologies de déploiement de SharePoint 2010](#bkmk_example_deployments_2010)  
  
    -   [Déploiements monoserveur](#bkmk_sharepoint2010_1server)  
  
    -   [Déploiement sur deux niveaux](#bkmk_sharepoint2010_2server)  
  
    -   [Déploiement sur trois niveaux](#bkmk_sharepoint2010_3server)  
  
    -   [Déploiement avec montée en puissance parallèle sur trois niveaux](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="sharepoint-2013-example-deployment-topologies"></a><a name="bkmk_example_deployments_2013"></a>Exemples de topologies de déploiement SharePoint 2013  
 L'option d'installation SQL Server **PowerPivot pour SharePoint** ne présente aucune dépendance par rapport à SharePoint. Elle n'utilise pas le modèle d'objet ou les interfaces SharePoint pour prendre en charge l'intégration. Par conséquent, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut être installé sur n'importe quel ordinateur exécutant Windows Server 2008 R2 ou une version ultérieure. Il peut s'agir, mais sans obligation, d'un serveur d'applications dans une batterie de serveurs SharePoint. L'une des étapes de configuration consiste à renvoyer Excel Services vers le serveur exécutant [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour l'équilibrage de charge et la tolérance de panne, il est recommandé d'installer et d'inscrire plusieurs serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exécutés en mode SharePoint.  
  
 Le mode SharePoint requiert SharePoint Server 2013 et utilise l’architecture de l’application de service SharePoint. ** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **  
  
 Les sections suivantes présentent les topologies de déploiement courantes :  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-three-server-deployment"></a><a name="bkmk_bi_Sharepoint2013_3tier"></a>PowerPivot pour SharePoint 2013 et Reporting Services déploiement à trois serveurs  
 Dans le déploiement à trois serveurs suivant, le moteur de base de données SQL Server, le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et SharePoint s'exécutent chacun sur un serveur distinct. Le package d'installation [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 (**spPowerPivot.msi**) doit être exécuté sur le serveur SharePoint.  
  
 ![Déploiement de 3 serveurs en mode SharePoint SSAS et SSRS](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "Déploiement de 3 serveurs en mode SharePoint SSAS et SSRS")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**2**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**1,3**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**4**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**5,5**|Exécutez le fichier **PowerPivot. msi** pour installer les fournisseurs de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , l’outil [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de configuration de, la Galerie et planifier l’actualisation des données.|  
|**6,3**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**Commission(7**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
 Les ![paramètres SharePoint](../../analysis-services/media/as-sharepoint2013-settings-gear.gif "Paramètres SharePoint") [soumettent des commentaires et des informations de contact via Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
###  <a name="powerpivot-for-sharepoint-2013-single-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_1server"></a>Déploiement d’un seul serveur PowerPivot pour SharePoint 2013  
 Un déploiement de serveur unique est utile à des fins de test mais n'est pas recommandée pour les déploiements de production.  
  
 Le diagramme suivant montre les composants qui font partie d'un déploiement d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur un seul serveur.  
  
 ![Déploiement mono-serveur de PowerPivot pour SharePoint](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "Déploiement mono-serveur de PowerPivot pour SharePoint")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**2**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**1,3**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
|**4**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
  
###  <a name="powerpivot-for-sharepoint-2013-two-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_2server"></a>Déploiement du serveur PowerPivot pour SharePoint 2013 2  
 Dans le déploiement à deux serveurs suivant, le moteur de base de données SQL Server et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint s'exécutent sur un serveur autre que celui sur lequel SharePoint est exécuté. Pour SharePoint 2013, le package d'installation [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] (**spPowerPivot.msi**) est installé sur le serveur SharePoint.  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)]étend SharePoint Server 2013 pour ajouter le traitement de l’actualisation des données côté serveur, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] les fournisseurs de données, la [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Galerie et la prise en charge de la gestion des classeurs et des classeurs Excel avec des modèles de données avancés.  
  
 Le package d'installation est disponible dans le cadre du Feature Pack [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Le Feature Pack peut être téléchargé à [!INCLUDE[msCoName](../../includes/msconame-md.md)] partir du centre de téléchargement à l’adresse [microsoft® SQL Server® 2014 PowerPivot® pour Microsoft® SharePoint®](https://go.microsoft.com/fwlink/?LinkID=296473) (lien<https://go.microsoft.com/fwlink/?LinkID=296473>hypertexte <https://go.microsoft.com/fwlink/?LinkID=296473>"" \t "_blank").  
  
 ![Déploiement de 2 serveurs en mode PowerPivot SSAS](../../analysis-services/media/as-powerpivot-mode-2server-deployment.gif "Déploiement de 2 serveurs en mode PowerPivot SSAS")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**2**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**1,3**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**4**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**5,5**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
###  <a name="powerpivot-for-sharepoint-2013-three-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_3server"></a>Déploiement du serveur PowerPivot pour SharePoint 2013 3  
 Dans le déploiement à trois serveurs suivant, le moteur de base de données SQL Server, le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et SharePoint s'exécutent chacun sur un serveur distinct. Le package d'installation [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 (spPowerPivot.msi) doit être installé sur le serveur SharePoint.  
  
 ![Déploiement de 3 serveurs en mode PowerPivot AS](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "Déploiement de 3 serveurs en mode PowerPivot AS")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**2**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**1,3**|Exécutez spPowerPivot.msi pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**4**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**5,5**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-single-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a>PowerPivot pour SharePoint 2013 et Reporting Services déploiement sur un seul serveur  
 Un déploiement de serveur unique est utile à des fins de test mais n'est pas recommandée pour les déploiements de production.  
  
 ![Déploiement d’un serveur en mode SharePoint SSAS et SSRS](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "Déploiement d’un serveur en mode SharePoint SSAS et SSRS")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**2**|Application de service PowerPivot. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**1,3**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**4**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**5,5**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
|**6,3**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-two-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a>PowerPivot pour SharePoint 2013 et Reporting Services déploiement sur deux serveurs  
 Dans le déploiement à deux serveurs suivant, le moteur de base de données SQL Server et le serveur Analysis Services en mode SharePoint s'exécutent sur un serveur autre que celui sur lequel SharePoint s'exécute. Le package d'installation PowerPivot pour SharePoint 2013 **(spPowerPivot.msi)** doit être exécuté sur le serveur SharePoint.  
  
 ![Déploiement de 2 serveurs en mode SharePoint SSAS et SSRS](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "Déploiement de 2 serveurs en mode SharePoint SSAS et SSRS")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**2**|Application de service PowerPivot. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**1,3**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**4**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**5,5**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de PowerPivot, la Galerie PowerPivot et l'actualisation des données de planification.|  
|**6,3**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**Commission(7**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
##  <a name="sharepoint-2010-example-deployment-topologies"></a><a name="bkmk_example_deployments_2010"></a>Exemples de topologies de déploiement SharePoint 2010  
 Le schéma suivant illustre les services et fournisseurs qui s'exécutent sur chaque niveau. Notez que le schéma inclut plusieurs services intégrés ; ces services sont requis pour certains scénarios de SQL Server BI. Excel Services, les services Banque d'informations sécurisés et les services d'émission de jetons Revendications vers Windows sont requis ou recommandés pour un déploiement de PowerPivot pour SharePoint ou de Reporting Services dans SharePoint. De plus, les fournisseurs de MSOLAP OLE DB et les services ADO.NET sont requis pour certains scénarios d'accès aux données PowerPivot. Vous pouvez Éventuellement installer Analysis Services sur le niveau de données, si vous souhaitez créer des rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] basés sur des bases de données model tabulaires  hébergées en dehors de SharePoint.  
  
 ![Schéma de l’architecture logique](../../../2014/sql-server/install/media/sql11bisetup.gif "Schéma de l’architecture logique")  
  
##  <a name="single-server-deployments"></a><a name="bkmk_sharepoint2010_1server"></a>Déploiements sur un seul serveur  
 Vous pouvez installer tous les composants serveur, notamment le niveau de données, sur un ordinateur unique. Cette configuration de déploiement est utile si vous évaluez le logiciel ou que vous développez des applications personnalisées qui incluent Reporting Services en mode SharePoint. Ce déploiement est le plus simple à configurer. Tous les composants étant installés sur le même ordinateur, moins de licences sont requises. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] et le [!INCLUDE[ssDE](../../includes/ssde-md.md)] sont installés comme une copie unique sous licence de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour installer toutes les fonctionnalités sur un seul serveur, vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] de manière séquentielle, sur le même serveur physique. Pour obtenir des instructions sur une configuration de serveur autonome, consultez [liste de vérification du déploiement : Reporting Services, Power View et PowerPivot pour SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
##  <a name="two-tier-deployment"></a><a name="bkmk_sharepoint2010_2server"></a>Déploiement sur deux niveaux  
 Un déploiement sur deux niveaux suit généralement le schéma suivant : SharePoint Server 2010 sur un ordinateur et le moteur de base de données SQL Server sur le deuxième ordinateur. Le déplacement du niveau de données sur un serveur dédié constitue la configuration la plus courante pour une batterie de 2 ordinateurs. Dans une batterie à deux niveaux, vous installez à la fois [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sur le serveur SharePoint. Tous les services Web sur le frontal et les services partagés dans le niveau d'applications s'exécutent sur le même serveur physique. Les étapes d'installation pour un déploiement à deux niveaux sont très semblables à un déploiement autonome, car vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] de manière séquentielle, sur le même serveur physique.  
  
##  <a name="three-tier-deployment"></a><a name="bkmk_sharepoint2010_3server"></a>Déploiement à trois niveaux  
 Un déploiement à trois niveaux sépare en général les services Web frontaux et les applications de traitement ou nécessitant beaucoup de mémoire. Sur cette topologie, vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] uniquement sur le serveur d'applications. Les services Web qui s'exécutent sur le Web frontal sont installés via des solutions déployées aux applications de la batterie, lors de la configuration du serveur, en tant que tâche consécutive à l'installation. Le schéma suivant illustre un déploiement sur 3 niveaux.  
  
 ![3-serveur topologie](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "3-serveur topologie")  
  
##  <a name="three-tier-scale-out-deployment"></a><a name="bkmk_sharepoint2010_scaleserver"></a>Déploiement avec montée en puissance parallèle à trois niveaux  
 Cette topologie illustre un déploiement avec montée en puissance parallèle qui exécute le même service partagé sur plusieurs serveurs, traitant ainsi un plus grand volume de demandes et fournissant une puissance de traitement supérieure pour les données PowerPivot ou les rapports Reporting Services. Dans le schéma ci-dessous, il existe trois clusters de serveurs d'applications, chacun exécutant une combinaison différente de services partagés. Dans un environnement SharePoint, la découverte de service et la disponibilité sont intégrées à la batterie de serveurs. L'équilibrage de charge sur plusieurs serveurs physiques exécutant la même application de service partagé fait partie de l'architecture du service partagé.  
  
 Lors du déploiement d'une batterie de plusieurs serveurs, veillez à suivre les instructions dans cet article SharePoint : [Plusieurs serveurs pour une batterie de serveurs à trois niveaux (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834).  
  
 ![Topologie 5 serveurs](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "Topologie 5 serveurs")  
  
## <a name="see-also"></a>Voir aussi  
 [Reporting Services l’installation en mode SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Installation de PowerPivot pour SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)   
 [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
