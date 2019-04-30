---
title: Serveur de rapports Reporting Services (mode SharePoint) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology:
- reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 246b0be389857e002e5c9e30cb899826234a58b7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63273840"
---
# <a name="reporting-services-report-server-sharepoint-mode"></a>Serveur de rapports Reporting Services (mode SharePoint)

Un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] configuré pour le **mode SharePoint** peut s'exécuter au sein d'un déploiement d'un produit SharePoint. Un serveur de rapports en mode SharePoint peut utiliser les fonctionnalités de collaboration et de gestion des rapports SharePoint et d'autres types de contenus [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Le mode SharePoint requiert l'installation de la version appropriée du complément d' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint sur vos serveurs Web frontaux SharePoint.  
  
Pour plus d'informations sur l'installation et la configuration, consultez les rubriques suivantes.  
  
- [Installer le Mode SharePoint de Reporting Services pour SharePoint 2013](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
- [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
- [Ajouter un serveur de rapports supplémentaire à une batterie de serveurs &#40;SSRS Scale-out&#41;](install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).  
  
 Pour plus d’informations sur les nouveautés introduite dans cette version, consultez la section « SharePoint » dans [What ' s New &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md).  
  
 **Dans cette rubrique :**  
  
-   [Synthèse des fonctionnalités](#bkmk_featuresum)  
  
-   [Mode connecté et mode local](#bkmk_connectedandlocal)  
  
-   [Fonctionnalités SharePoint non prises en charge](#bkmk_unsupportedsharepoint)  
  
-   [Combinaisons prises en charge du complément SharePoint et de Report Server](#bkmk_supportedcombinations)  
  
-   [Composants qui fournissent l'intégration](#bkmk_components)  
  
-   [Observations relatives au langage](#bkmk_language)  
  
-   [Tâches associées](#bkmk_relatedtasks)  
  
##  <a name="bkmk_featuresum"></a> Synthèse des fonctionnalités

 Configurer un serveur de rapports pour qu'il s'exécute en mode intégré SharePoint fournit les fonctionnalités supplémentaires ci-dessous, qui sont disponibles uniquement lorsque vous déployez un serveur de rapports dans ce mode :  
  
-   Utilisez les fonctionnalités de SharePoint de gestion de documents et de collaboration, y compris les alertes. Un site SharePoint fournit un portail unifié permettant d'accéder à tous les éléments de rapport et de les gérer dans un seul emplacement.  
  
-   Utilisez les autorisations SharePoint et les fournisseurs d'authentification pour contrôler l'accès aux rapports, aux modèles et aux autres éléments.  
  
-   Utilisez les topologies de déploiement SharePoint pour distribuer des rapports via une connexion Internet en dehors du pare-feu. Un serveur de rapports fournit des services de traitement de rapports et de données dans le cadre d'un déploiement SharePoint plus vaste, configuré pour l'accès à Internet.  
  
-   Gérez des rapports, des modèles, des sources de données, des planifications et un historique de rapport dans des pages d'application personnalisées sur un site SharePoint. Vous pouvez définir des propriétés, des planifications et des abonnements, ainsi que créer et gérer un historique de rapport sur un site SharePoint de la même manière que vous les créez et gérez à partir d'autres outils dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Publiez ou téléchargez des rapports, des modèles de rapport, des ressources et des fichiers de sources de données partagées dans une bibliothèque SharePoint, y compris Report Center dans Office SharePoint Server.  
  
     Utilisez le Concepteur de rapports, le Générateur de modèles et le Générateur de rapports pour créer des rapports et des sources de données à publier directement dans une bibliothèque SharePoint. Vous pouvez également utiliser l'action Télécharger sur un site SharePoint pour ajouter des définitions de rapport et des modèles de rapport quelconques dans une bibliothèque SharePoint.  
  
     Comme le serveur de rapports traite les définitions de rapport de la même manière, quel que soit le mode serveur utilisé, les données et la mise en page des rapports ne sont pas affectées par le mode serveur. Tout rapport que vous pouvez exécuter sur un serveur de rapports en mode natif peut être exécuté sur un serveur de rapports configuré pour le mode intégré SharePoint.  
  
-   Abonnez-vous à des rapports et livrez-les dans une bibliothèque SharePoint à l'aide d'une nouvelle extension de remise SharePoint. Vous pouvez également livrer des rapports par courrier électronique ou dans un dossier partagé. Les extensions de remise du serveur de rapports sont utilisées pour livrer les rapports. Vous pouvez créer des abonnements pilotés par les données pour une distribution de rapport à grande échelle à l'aide de données d'abonné interrogées au moment de l'exécution.  
  
-   Vous pouvez ajouter aux pages SharePoint un composant WebPart Visionneuse de rapports pour afficher un rapport à l'intérieur de votre application Web SharePoint. Le composant WebPart inclut des fonctionnalités de navigation entre les pages, de recherche, d'impression et d'exportation.  
  
-   Programmez un nouveau point de terminaison SOAP pour créer des applications personnalisées qui s'intègrent à un site SharePoint. Vous pouvez également utiliser le fournisseur WMI (Windows Management Instrumentation) mis à jour pour configurer par programmation une instance de serveur de rapports qui s'exécute en mode intégré SharePoint.  
  
-   Rapports de services Microsoft Access en mode connecté.  
  
-   Zones AAM (mappages d'accès de substitution), déploiements exposés à Internet et jetons utilisateur SharePoint pour les listes SharePoint.  
  
##  <a name="bkmk_connectedandlocal"></a> Mode connecté et mode local

 La version SQL Server 2008 R2 a introduit un nouveau *mode local* pour consulter des rapports d’un serveur SharePoint 2010 qui inclut le complément Microsoft SQL Server 2008 R2 Reporting Services (ou version ultérieure) pour les produits SharePoint 2010 installés.  
  
-   *Mode local*: Le mode local permet un rendu local des rapports à partir de la bibliothèque de documents SharePoint sans intégration avec un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint est requis, mais un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne l'est pas. Le complément peut être installé de différentes façons, notamment avec l'Outil de préparation des produits SharePoint 2010. Pour plus d’informations sur le mode local, consultez [Rapports en mode local et Mode rapports connecté dans la visionneuse de rapports &#40;Reporting Services en SharePoint Mode&#41; ](../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md) et [où trouver le complément Reporting Services pour les produits SharePoint](install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
-   *Mode connecté*: En mode connecté est pris en charge en intégrant un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] serveur de rapports dans la batterie de serveurs SharePoint à l’aide de l’Administration centrale SharePoint. L’intégration avec un serveur de rapports permet de générer des rapports complets end-to-end, en fournissant les fonctionnalités de collaboration de SharePoint 2010 et les fonctionnalités de serveur d’un serveur de rapports, notamment : Abonnements, instantanés et traitement par le serveur.  
  
##  <a name="bkmk_unsupportedsharepoint"></a> Fonctionnalités SharePoint non prises en charge

 Certaines fonctionnalités SharePoint ne sont pas disponibles en mode intégré. La liste suivante présente les fonctionnalités SharePoint avec lesquelles [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne s'intègre pas directement :  
  
-   Service Banque d'informations sécurisé.  
  
-   Vous ne pouvez pas utiliser l'intégration du calendrier Outlook dans SharePoint ni la planification SharePoint pour les fichiers de Reporting Services dans une bibliothèque de documents.  
  
-   Catalogue de données métier SharePoint.  
  
-   La personnalisation SharePoint n'est pas prise en charge sur les pages de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . L'intégration Report Server n'est pas prise en charge si l'application Web SharePoint est activée pour l'accès anonyme.  
  
-   SQL Server Reporting Services ne prend **pas** en charge le contrôle de version de bibliothèque de documents SharePoint. Si vous enregistrez des éléments de rapport dans une bibliothèque de documents pour laquelle l’option Historique des versions du document est activée, les fonctionnalités de Reporting Services ne fonctionnent pas correctement et génèrent des erreurs dans le journal ULS. L'exemple suivant montre une erreur dans le journal ULS :  
  
    -   « …une source de données associée au rapport a été désactivée ».  
  
     L’historique des versions de la bibliothèque de documents est configuré dans la page Paramètres de contrôle de version de Paramètres de la bibliothèque.  
  
##  <a name="bkmk_supportedcombinations"></a> Combinaisons prises en charge du complément SharePoint et de Report Server

 Certaines fonctionnalités ne sont pas prises en charge dans toutes les combinaisons de serveur de rapports, complément Reporting Services pour SharePoint et produits SharePoint. Pour plus d’informations, consultez [pris en charge les combinaisons de SharePoint et le serveur Reporting Services et complément &#40;SQL Server 2014&#41;](install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
> [!NOTE]  
>  La version correcte du complément Reporting Services doit être utilisée avec la version correspondante des produits SharePoint.  
  
##  <a name="bkmk_components"></a> Composants qui fournissent l'intégration

 Pour associer les serveurs dans un déploiement unique, vous intégrez une installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] à une instance de produits SharePoint.  
  
 L’intégration est fournie par le biais de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et du complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint. Le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est un composant en distribution libre que vous pouvez télécharger, puis installer sur un serveur qui exécute la version appropriée de SharePoint.  
  
> [!TIP]  
>  Certaines fonctionnalités ne sont pas prises en charge dans toutes les combinaisons de serveur de rapports, complément Reporting Services pour SharePoint et produits SharePoint. Pour plus d’informations, consultez [pris en charge les combinaisons de SharePoint et le serveur Reporting Services et complément &#40;SQL Server 2014&#41;](install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   Dans SharePoint, le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit le point de terminaison proxy ReportServer, un composant WebPart Visionneuse de rapports et des pages d’application afin que vous puissiez afficher, stocker et gérer le contenu du serveur de rapports sur un site ou une batterie de serveurs SharePoint.  
  
-   Sur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , des fichiers programme mis à jour, un point de terminaison SOAP, ainsi que des extensions de sécurité et de remise personnalisées sont fournis. Le serveur de rapports doit être configuré pour s'exécuter en mode intégré SharePoint, dédié exclusivement à la prise en charge de la remise des rapports et de l'accès aux rapports par le biais de votre site SharePoint.  
  
 Une fois que vous avez installé le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans SharePoint et configuré les deux serveurs pour l'intégration, vous pouvez télécharger ou publier les types de contenu du serveur de rapports vers une bibliothèque SharePoint, puis afficher et gérer ces documents à partir d'un site SharePoint. Le téléchargement ou la publication du contenu du serveur de rapports constitue une première étape importante ; le composant WebPart et les pages deviennent accessibles lorsque vous sélectionnez des définitions de rapport (.rdl), des modèles de rapport (.smdl) et des sources de données partagées (.rsds) sur un site SharePoint.  
  
##  <a name="bkmk_language"></a> Observations relatives au langage

 [!INCLUDE[SPF2010](../includes/spf2010-md.md)] et [!INCLUDE[SPS2010](../includes/sps2010-md.md)] sont disponibles dans beaucoup plus de langues que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 Lorsque vous configurez un serveur de rapports pour qu'il s'exécute dans un déploiement d'un produit SharePoint, vous pouvez éventuellement constater une combinaison de langues. L'interface utilisateur, la documentation et les messages apparaissent dans les langues suivantes :  
  
-   L'ensemble des pages, des outils, des erreurs, des avertissements et des messages de l'application qui proviennent de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] apparaissent dans la langue utilisée par l'instance de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans l'une des langues [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Les pages d'application que vous ouvrez sur un site SharePoint, le composant WebPart Visionneuse de rapports et le Générateur de rapports s'afficheront dans l'une des langues prises en charge pour le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Pour examiner la liste des langues prises en charge, accédez à [Téléchargements SQL Server](https://msdn.microsoft.com/sql/downloads/) et recherchez la page de téléchargement pour le complément [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Les sites SharePoint, l'administration centrale de SharePoint, l'aide en ligne et les messages sont disponibles dans les langues prises en charge par les produits Office Server.  
  
 Si la langue de votre produit ou technologie SharePoint diffère de la langue du serveur de rapports, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] essaie d'utiliser une langue de la même famille de langues qui correspond le mieux. Si aucun substitut proche n'est disponible, le serveur de rapports utilise l'anglais.  
  
##  <a name="bkmk_relatedtasks"></a> Tâches associées

 Le tableau suivant récapitule les tâches liées à un serveur de rapports en mode SharePoint [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] :  
  
|**Tâche**|**Lien**|  
|--------------|--------------|  
|Procédures détaillées pour installer et configurer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint.|[Installer Reporting Services en Mode SharePoint pour SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) et [ajouter un serveur de rapports supplémentaire à une batterie de serveurs &#40;SSRS Scale-out&#41;](install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).|  
|Effectuez votre déploiement SharePoint [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] avec montée en puissance parallèle en ajoutant des serveurs de rapports supplémentaires.|[Ajouter un serveur de rapports supplémentaire à une batterie de serveurs &#40;SSRS Scale-out&#41; ](install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) et [Deployment Topologies for SQL Server BI Features in SharePoint](../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md) .|  
|Ajoutez des serveurs web frontaux SharePoint supplémentaires dotés des composants [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour l’affichage et les éléments de rapport.|[Ajouter un serveur Web frontal Reporting Services supplémentaire à une batterie](install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Configurez la messagerie électronique pour les fonctionnalités d'abonnement et d'alertes de données [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[Configurer la messagerie électronique pour une application de service Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|  
|Les informations récentes pour cette version s'appuient sur TechNet Wiki.|[Conseils, astuces et dépannage pour SQL Server 2012 Reporting Services](https://go.microsoft.com/fwlink/?LinkId=221297).|  
  
## <a name="see-also"></a>Voir aussi  
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41; ](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) [matérielle et logicielle requise pour Reporting Services en Mode SharePoint](../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md) [Composant WebPart Visionneuse de rapports sur un Site SharePoint](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md)