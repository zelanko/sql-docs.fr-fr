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
ms.openlocfilehash: d1d8d503fc5020fb9d44bb8daa4be79abd00dc0d
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952642"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>Topologies de déploiement pour les fonctionnalités SQL Server BI dans SharePoint
  Cette rubrique décrit les topologies courantes pour l'installation des fonctionnalités SQL Server Business Intelligence de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] dans les environnements SharePoint 2010 et SharePoint 2013. Par exemple, des installations à trois niveaux et de serveur unique.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **Dans cette rubrique :**  
  
-   [Exemples de topologies de déploiement SharePoint 2013](#bkmk_example_deployments_2013)  
  
    -   [PowerPivot pour SharePoint 2013 et Reporting Services déploiement à trois serveurs](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [Déploiement d’un seul serveur PowerPivot pour SharePoint 2013](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [Déploiement du serveur PowerPivot pour SharePoint 2013 2](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [Déploiement du serveur PowerPivot pour SharePoint 2013 3](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [PowerPivot pour SharePoint 2013 et Reporting Services déploiement sur un seul serveur](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [PowerPivot pour SharePoint 2013 et Reporting Services déploiement sur deux serveurs](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [Exemples de topologies de déploiement SharePoint 2010](#bkmk_example_deployments_2010)  
  
    -   [Déploiements sur un seul serveur](#bkmk_sharepoint2010_1server)  
  
    -   [Déploiement sur deux niveaux](#bkmk_sharepoint2010_2server)  
  
    -   [Déploiement à trois niveaux](#bkmk_sharepoint2010_3server)  
  
    -   [Déploiement avec montée en puissance parallèle à trois niveaux](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="bkmk_example_deployments_2013"></a>Exemples de topologies de déploiement SharePoint 2013  
 L'option d'installation SQL Server **PowerPivot pour SharePoint** ne présente aucune dépendance par rapport à SharePoint. Elle n'utilise pas le modèle d'objet ou les interfaces SharePoint pour prendre en charge l'intégration. Par conséquent, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut être installé sur n'importe quel ordinateur exécutant Windows Server 2008 R2 ou une version ultérieure. Il peut s'agir, mais sans obligation, d'un serveur d'applications dans une batterie de serveurs SharePoint. L'une des étapes de configuration consiste à renvoyer Excel Services vers le serveur exécutant [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour l'équilibrage de charge et la tolérance de panne, il est recommandé d'installer et d'inscrire plusieurs serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exécutés en mode SharePoint.  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] le mode SharePoint** requiert sharepoint server 2013 et utilise l’architecture de l’application de service SharePoint.  
  
 Les sections suivantes présentent les topologies de déploiement courantes :  
  
###  <a name="bkmk_bi_Sharepoint2013_3tier"></a>PowerPivot pour SharePoint 2013 et Reporting Services déploiement à trois serveurs  
 Dans le déploiement à trois serveurs suivant, le moteur de base de données SQL Server, le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et SharePoint s'exécutent chacun sur un serveur distinct. Le package d'installation [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 (**spPowerPivot.msi**) doit être exécuté sur le serveur SharePoint.  
  
 Déploiement ![de serveur en mode SharePoint SSAS et SSRS 3 déploiement](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "de") serveur  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**(6)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(7)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
 ![Paramètres]SharePoint paramètres(https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint") [Envoyer des commentaires et des informations de contact via Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
###  <a name="bkmk_powerpivot_sharepoint2013_1server"></a>Déploiement d’un seul serveur PowerPivot pour SharePoint 2013  
 Un déploiement de serveur unique est utile à des fins de test mais n'est pas recommandée pour les déploiements de production.  
  
 Le diagramme suivant montre les composants qui font partie d'un déploiement d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur un seul serveur.  
  
 Déploiement ![PowerPivot pour SharePoint un seul serveur](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot pour SharePoint déploiement sur un seul serveur")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
|**(4)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_2server"></a>Déploiement du serveur PowerPivot pour SharePoint 2013 2  
 Dans le déploiement à deux serveurs suivant, le moteur de base de données SQL Server et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint s'exécutent sur un serveur autre que celui sur lequel SharePoint est exécuté. Pour SharePoint 2013, le package d'installation [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] (**spPowerPivot.msi**) est installé sur le serveur SharePoint.  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] étend SharePoint Server 2013 pour ajouter le traitement de l’actualisation des données côté serveur, les fournisseurs de données, la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et la prise en charge de la gestion des classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et des classeurs Excel avec des modèles de données avancés.  
  
 Le package d'installation est disponible dans le cadre du Feature Pack [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Le Feature Pack peut être téléchargé à partir du centre de téléchargement [!INCLUDE[msCoName](../../includes/msconame-md.md)] à l’adresse [microsoft® SQL Server® 2014 PowerPivot® pour microsoft® SharePoint®](https://go.microsoft.com/fwlink/?LinkID=296473) (HYPERLINK "<https://go.microsoft.com/fwlink/?LinkID=296473>" \t "_ blank" <https://go.microsoft.com/fwlink/?LinkID=296473>).  
  
 ![Déploiement de serveur en mode 2 SSAS](https://docs.microsoft.com/analysis-services/analysis-services/media/as-powerpivot-mode-2server-deployment.gif "Déploiement de serveur en mode 2 SSAS")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**(4)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(5)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_3server"></a>Déploiement du serveur PowerPivot pour SharePoint 2013 3  
 Dans le déploiement à trois serveurs suivant, le moteur de base de données SQL Server, le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et SharePoint s'exécutent chacun sur un serveur distinct. Le package d'installation [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 (spPowerPivot.msi) doit être installé sur le serveur SharePoint.  
  
 ![En tant que déploiement du serveur MODE3 PowerPivot](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "en tant que déploiement de serveur MODE3 PowerPivot")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|Exécutez spPowerPivot.msi pour installer les fournisseurs de données, l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et planifier l'actualisation des données.|  
|**(4)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(5)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a>PowerPivot pour SharePoint 2013 et Reporting Services déploiement sur un seul serveur  
 Un déploiement de serveur unique est utile à des fins de test mais n'est pas recommandée pour les déploiements de production.  
  
 Déploiement serveur ![en mode SharePoint SSAS et SSRS 1 déploiement serveur](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SSAS et SSRS mode SharePoint mode 1")  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service PowerPivot. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
|**(6)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a>PowerPivot pour SharePoint 2013 et Reporting Services déploiement sur deux serveurs  
 Dans le déploiement à deux serveurs suivant, le moteur de base de données SQL Server et le serveur Analysis Services en mode SharePoint s'exécutent sur un serveur autre que celui sur lequel SharePoint s'exécute. Le package d'installation PowerPivot pour SharePoint 2013 **(spPowerPivot.msi)** doit être exécuté sur le serveur SharePoint.  
  
 Déploiement ![de serveur en mode SharePoint SSAS et SSRS 2 déploiement](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "de serveurs SSAS et SSRS en mode SharePoint (2") )  
  
|||  
|-|-|  
|**(1)**|Application Excel Services. L'application de service est créée dans le cadre de l'installation de SharePoint.|  
|**(2)**|Application de service PowerPivot. Le nom par défaut est **Application de service PowerPivot par défaut**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Installez le complément Reporting Services pour SharePoint à partir du support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou du pack de fonctionnalités de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Exécutez **spPowerPivot.msi** pour installer les fournisseurs de données, l'outil de configuration de PowerPivot, la Galerie PowerPivot et l'actualisation des données de planification.|  
|**(6)**|Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint Configurez l'application Excel Services dans les **Paramètres du modèle de données** pour utiliser ce serveur.|  
|**(7)**|Bases de données de contenu, de configuration et d'application de service SharePoint.|  
  
##  <a name="bkmk_example_deployments_2010"></a>Exemples de topologies de déploiement SharePoint 2010  
 Le schéma suivant illustre les services et fournisseurs qui s'exécutent sur chaque niveau. Notez que le schéma inclut plusieurs services intégrés ; ces services sont requis pour certains scénarios de SQL Server BI. Excel Services, les services Banque d'informations sécurisés et les services d'émission de jetons Revendications vers Windows sont requis ou recommandés pour un déploiement de PowerPivot pour SharePoint ou de Reporting Services dans SharePoint. De plus, les fournisseurs de MSOLAP OLE DB et les services ADO.NET sont requis pour certains scénarios d'accès aux données PowerPivot. Vous pouvez Éventuellement installer Analysis Services sur le niveau de données, si vous souhaitez créer des rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] basés sur des bases de données model tabulaires  hébergées en dehors de SharePoint.  
  
 Diagramme de l’architecture(../../../2014/sql-server/install/media/sql11bisetup.gif "logique") du ![diagramme d’architecture logique]  
  
##  <a name="bkmk_sharepoint2010_1server"></a>Déploiements sur un seul serveur  
 Vous pouvez installer tous les composants serveur, notamment le niveau de données, sur un ordinateur unique. Cette configuration de déploiement est utile si vous évaluez le logiciel ou que vous développez des applications personnalisées qui incluent Reporting Services en mode SharePoint. Ce déploiement est le plus simple à configurer. Tous les composants étant installés sur le même ordinateur, moins de licences sont requises. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] et le [!INCLUDE[ssDE](../../includes/ssde-md.md)] sont installés comme une copie unique sous licence de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour installer toutes les fonctionnalités sur un seul serveur, vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] de manière séquentielle, sur le même serveur physique. Pour obtenir des instructions sur une configuration de serveur autonome, consultez la liste de vérification [Deployment : Reporting Services, Power View et PowerPivot pour SharePoint @ no__t-0.  
  
##  <a name="bkmk_sharepoint2010_2server"></a>Déploiement sur deux niveaux  
 Un déploiement sur deux niveaux suit généralement le schéma suivant : SharePoint Server 2010 sur un ordinateur et le moteur de base de données SQL Server sur le deuxième ordinateur. Le déplacement du niveau de données sur un serveur dédié constitue la configuration la plus courante pour une batterie de 2 ordinateurs. Dans une batterie à deux niveaux, vous installez à la fois [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sur le serveur SharePoint. Tous les services Web sur le frontal et les services partagés dans le niveau d'applications s'exécutent sur le même serveur physique. Les étapes d'installation pour un déploiement à deux niveaux sont très semblables à un déploiement autonome, car vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] de manière séquentielle, sur le même serveur physique.  
  
##  <a name="bkmk_sharepoint2010_3server"></a>Déploiement à trois niveaux  
 Un déploiement à trois niveaux sépare en général les services Web frontaux et les applications de traitement ou nécessitant beaucoup de mémoire. Sur cette topologie, vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] uniquement sur le serveur d'applications. Les services Web qui s'exécutent sur le Web frontal sont installés via des solutions déployées aux applications de la batterie, lors de la configuration du serveur, en tant que tâche consécutive à l'installation. Le schéma suivant illustre un déploiement sur 3 niveaux.  
  
 ![3-Server topologie](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "3-Server topologie")  
  
##  <a name="bkmk_sharepoint2010_scaleserver"></a>Déploiement avec montée en puissance parallèle à trois niveaux  
 Cette topologie illustre un déploiement avec montée en puissance parallèle qui exécute le même service partagé sur plusieurs serveurs, traitant ainsi un plus grand volume de demandes et fournissant une puissance de traitement supérieure pour les données PowerPivot ou les rapports Reporting Services. Dans le schéma ci-dessous, il existe trois clusters de serveurs d'applications, chacun exécutant une combinaison différente de services partagés. Dans un environnement SharePoint, la découverte de service et la disponibilité sont intégrées à la batterie de serveurs. L'équilibrage de charge sur plusieurs serveurs physiques exécutant la même application de service partagé fait partie de l'architecture du service partagé.  
  
 Lors du déploiement d’une batterie de plusieurs serveurs, veillez à suivre les instructions de cet article SharePoint : [Plusieurs serveurs pour une batterie à trois niveaux (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834).  
  
 ![5-serveur topologie](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "5-serveur topologie")  
  
## <a name="see-also"></a>Voir aussi  
 [Reporting Services de l’installation &#40;en mode SharePoint de SharePoint&#41;2010 et SharePoint 2013](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 @No__t [installation de PowerPivot pour SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)-1  
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
