---
title: Topologies de déploiement pour les fonctionnalités SQL Server BI dans SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2bcb706eda464730d978d0098281c2ebcd2336ed
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53365761"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>Topologies de déploiement pour les fonctionnalités SQL Server BI dans SharePoint
  Cette rubrique décrit les topologies courantes pour l'installation des fonctionnalités SQL Server Business Intelligence de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] dans les environnements SharePoint 2010 et SharePoint 2013. Par exemple, des installations à trois niveaux et de serveur unique.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **Dans cette rubrique :**  
  
-   [Topologies de déploiement de SharePoint 2013 exemple](#bkmk_example_deployments_2013)  
  
    -   [Déploiement à trois serveurs de PowerPivot pour SharePoint 2013 et Reporting Services](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [PowerPivot pour SharePoint 2013 déploiement mono-serveur](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [PowerPivot pour le déploiement à deux serveurs SharePoint 2013](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [PowerPivot pour le déploiement à trois serveurs SharePoint 2013](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [PowerPivot pour SharePoint 2013 et Reporting Services déploiement monoserveur](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [Déploiement à deux serveurs de PowerPivot pour SharePoint 2013 et Reporting Services](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [Topologies de déploiement de SharePoint 2010 exemple](#bkmk_example_deployments_2010)  
  
    -   [Déploiements de serveur unique](#bkmk_sharepoint2010_1server)  
  
    -   [Déploiement sur deux niveaux](#bkmk_sharepoint2010_2server)  
  
    -   [Déploiement à trois niveaux](#bkmk_sharepoint2010_3server)  
  
    -   [Déploiement de montée en puissance à trois niveaux](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="bkmk_example_deployments_2013"></a> Topologies de déploiement de SharePoint 2013 exemple  
 L'option d'installation SQL Server **PowerPivot pour SharePoint** ne présente aucune dépendance par rapport à SharePoint. Elle n'utilise pas le modèle d'objet ou les interfaces SharePoint pour prendre en charge l'intégration. Par conséquent, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut être installé sur n'importe quel ordinateur exécutant Windows Server 2008 R2 ou une version ultérieure. Il peut s'agir, mais sans obligation, d'un serveur d'applications dans une batterie de serveurs SharePoint. L'une des étapes de configuration consiste à renvoyer Excel Services vers le serveur exécutant [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour l'équilibrage de charge et la tolérance de panne, il est recommandé d'installer et d'inscrire plusieurs serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exécutés en mode SharePoint.  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint** requiert SharePoint server 2013 et utilise l’architecture d’Application de Service SharePoint.  
  
 Les sections suivantes présentent les topologies de déploiement courantes :  
  
###  <a name="bkmk_bi_Sharepoint2013_3tier"></a> Déploiement à trois serveurs de PowerPivot pour SharePoint 2013 et Reporting Services  
 Dans le déploiement à trois serveurs suivant, le moteur de base de données SQL Server, le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et SharePoint s'exécutent chacun sur un serveur distinct. Le package d'installation [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 (**spPowerPivot.msi**) doit être exécuté sur le serveur SharePoint.  
  
 ![Mode SharePoint SSAS et SSRS 3 déploiement de serveur](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "mode SharePoint SSAS et SSRS 3 déploiement de serveur")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**(6)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(7)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
 ![Paramètres SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "paramètres SharePoint") [envoyer des commentaires et des informations via Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
###  <a name="bkmk_powerpivot_sharepoint2013_1server"></a> PowerPivot pour SharePoint 2013 déploiement mono-serveur  
 Un déploiement de serveur unique est utile à des fins de test mais n'est pas recommandée pour les déploiements de production.  
  
 Le diagramme suivant montre les composants qui font partie d'un déploiement d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur un seul serveur.  
  
 ![PowerPivot pour le déploiement de serveur SharePoint unique](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot pour le déploiement mono-serveur de SharePoint")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
|**(4)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_2server"></a> PowerPivot pour le déploiement à deux serveurs SharePoint 2013  
 Dans le déploiement à deux serveurs suivant, le moteur de base de données SQL Server et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint s'exécutent sur un serveur autre que celui sur lequel SharePoint est exécuté. Pour SharePoint 2013, le package d'installation [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] (**spPowerPivot.msi**) est installé sur le serveur SharePoint.  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] étend SharePoint Server 2013 afin d’ajouter l’actualisation des données côté serveur de traitement, fournisseurs de données, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] galerie et la prise en charge de la gestion de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] classeurs et des classeurs Excel avec des modèles de données avancés.  
  
 Le package d'installation est disponible dans le cadre du Feature Pack [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Le feature pack peut être téléchargé à partir la [!INCLUDE[msCoName](../../includes/msconame-md.md)] centre de téléchargement à [PowerPivot® Microsoft® SQL Server® 2014 pour Microsoft® SharePoint®](https://go.microsoft.com/fwlink/?LinkID=296473) (lien hypertexte «<https://go.microsoft.com/fwlink/?LinkID=296473>"\t « _blank » <https://go.microsoft.com/fwlink/?LinkID=296473>).  
  
 ![Déploiement de serveur SSAS PowerPivot Mode 2](../../../2014/analysis-services/media/as-powerpivot-mode-2server-deployment.gif "déploiement de serveur SSAS PowerPivot Mode 2")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**(4)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(5)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_3server"></a> PowerPivot pour le déploiement à trois serveurs SharePoint 2013  
 Dans le déploiement à trois serveurs suivant, le moteur de base de données SQL Server, le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et SharePoint s'exécutent chacun sur un serveur distinct. Le package d'installation [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 (spPowerPivot.msi) doit être installé sur le serveur SharePoint.  
  
 ![En tant que déploiement de serveur PowerPivot Mode3](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "en tant que déploiement de serveur PowerPivot Mode3")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Application de service. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|Exécutez spPowerPivot.msi pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**(4)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(5)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a> PowerPivot pour SharePoint 2013 et Reporting Services déploiement monoserveur  
 Un déploiement de serveur unique est utile à des fins de test mais n'est pas recommandée pour les déploiements de production.  
  
 ![Mode SharePoint SSAS et SSRS 1 serveur de déploiement](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SharePoint SSAS et SSRS en mode 1 déploiement de serveur")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service PowerPivot. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
|**(6)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a> Déploiement à deux serveurs de PowerPivot pour SharePoint 2013 et Reporting Services  
 Dans le déploiement à deux serveurs suivant, le moteur de base de données SQL Server et le serveur Analysis Services en mode SharePoint s'exécutent sur un serveur autre que celui sur lequel SharePoint s'exécute. Le package d'installation PowerPivot pour SharePoint 2013 **(spPowerPivot.msi)** doit être exécuté sur le serveur SharePoint.  
  
 ![SSAS et SSRS en Mode 2 de SharePoint Server déploiement](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "SSAS et le déploiement de SSRS en Mode 2 de SharePoint Server")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service PowerPivot. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de PowerPivot, la Galerie PowerPivot et l'actualisation des données de planification.|  
|**(6)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(7)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
##  <a name="bkmk_example_deployments_2010"></a> Topologies de déploiement de SharePoint 2010 exemple  
 Le schéma suivant illustre les services et fournisseurs qui s'exécutent sur chaque niveau. Notez que le schéma inclut plusieurs services intégrés ; ces services sont requis pour certains scénarios de SQL Server BI. Excel Services, les services Banque d'informations sécurisés et les services d'émission de jetons Revendications vers Windows sont requis ou recommandés pour un déploiement de PowerPivot pour SharePoint ou de Reporting Services dans SharePoint. De plus, les fournisseurs de MSOLAP OLE DB et les services ADO.NET sont requis pour certains scénarios d'accès aux données PowerPivot. Vous pouvez Éventuellement installer Analysis Services sur le niveau de données, si vous souhaitez créer des rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] basés sur des bases de données model tabulaires  hébergées en dehors de SharePoint.  
  
 ![Diagramme d’architecture logique](../../../2014/sql-server/install/media/sql11bisetup.gif "diagramme d’architecture logique")  
  
##  <a name="bkmk_sharepoint2010_1server"></a> Déploiements de serveur unique  
 Vous pouvez installer tous les composants serveur, notamment le niveau de données, sur un ordinateur unique. Cette configuration de déploiement est utile si vous évaluez le logiciel ou que vous développez des applications personnalisées qui incluent Reporting Services en mode SharePoint. Ce déploiement est le plus simple à configurer. Tous les composants étant installés sur le même ordinateur, moins de licences sont requises. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] et le [!INCLUDE[ssDE](../../includes/ssde-md.md)] sont installés comme une copie unique sous licence de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour installer toutes les fonctionnalités sur un seul serveur, vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] de manière séquentielle, sur le même serveur physique. Pour obtenir des instructions sur une configuration de serveur autonome, consultez [liste de vérification de déploiement : Reporting Services, Power View et PowerPivot pour SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
##  <a name="bkmk_sharepoint2010_2server"></a> Déploiement sur deux niveaux  
 Un déploiement sur deux niveaux suit généralement le schéma suivant : SharePoint Server 2010 sur un ordinateur et le moteur de base de données SQL Server sur le deuxième ordinateur. Le déplacement du niveau de données sur un serveur dédié constitue la configuration la plus courante pour une batterie de 2 ordinateurs. Dans une batterie à deux niveaux, vous installez à la fois [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sur le serveur SharePoint. Tous les services Web sur le frontal et les services partagés dans le niveau d'applications s'exécutent sur le même serveur physique. Les étapes d'installation pour un déploiement à deux niveaux sont très semblables à un déploiement autonome, car vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] de manière séquentielle, sur le même serveur physique.  
  
##  <a name="bkmk_sharepoint2010_3server"></a> Déploiement à trois niveaux  
 Un déploiement à trois niveaux sépare en général les services Web frontaux et les applications de traitement ou nécessitant beaucoup de mémoire. Sur cette topologie, vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] uniquement sur le serveur d'applications. Les services Web qui s'exécutent sur le Web frontal sont installés via des solutions déployées aux applications de la batterie, lors de la configuration du serveur, en tant que tâche consécutive à l'installation. Le schéma suivant illustre un déploiement sur 3 niveaux.  
  
 ![topologie de 3 serveurs](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "3 serveurs topologie")  
  
##  <a name="bkmk_sharepoint2010_scaleserver"></a> Déploiement de montée en puissance à trois niveaux  
 Cette topologie illustre un déploiement avec montée en puissance parallèle qui exécute le même service partagé sur plusieurs serveurs, traitant ainsi un plus grand volume de demandes et fournissant une puissance de traitement supérieure pour les données PowerPivot ou les rapports Reporting Services. Dans le schéma ci-dessous, il existe trois clusters de serveurs d'applications, chacun exécutant une combinaison différente de services partagés. Dans un environnement SharePoint, la découverte de service et la disponibilité sont intégrées à la batterie de serveurs. L'équilibrage de charge sur plusieurs serveurs physiques exécutant la même application de service partagé fait partie de l'architecture du service partagé.  
  
 Lors du déploiement d'une batterie de plusieurs serveurs, veillez à suivre les instructions dans cet article SharePoint : [Plusieurs serveurs pour une batterie de serveurs à trois niveaux (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834).  
  
 ![topologie 5 serveurs](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "topologie 5 serveurs")  
  
## <a name="see-also"></a>Voir aussi  
 [Installation en Mode SharePoint de Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Installation PowerPivot pour SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)   
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
