---
title: Report Server Reporting Services (Mode SharePoint) | Documents Microsoft
ms.custom: 
ms.date: 09/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a8cd1bd00ec92535fff73c5eaa4ff9bbe9274ef2
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---

# <a name="reporting-services-report-server-sharepoint-mode"></a>Serveur de rapports Reporting Services (mode SharePoint)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)])

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Un serveur de rapports Reporting Services configuré pour **en SharePoint Mode** peut s’exécuter dans un déploiement d’un produit SharePoint. Un serveur de rapports en mode SharePoint peut utiliser les fonctionnalités de collaboration et de gestion des rapports SharePoint et d'autres types de contenus [!INCLUDE[ssRSnfoversion_md](../../includes/ssrsnoversion-md.md)] . Mode SharePoint requiert l’installation de la version appropriée du complément Reporting Services pour les produits SharePoint sur votre Web frontaux SharePoint.  
  
> [!NOTE]
> Intégration de Reporting Services avec SharePoint n’est plus disponible après SQL Server 2016.

 Pour plus d'informations sur l'installation et la configuration, consultez les rubriques suivantes.  
  
-   [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c).  
  
-   [Ajouter un serveur de rapports supplémentaires à une batterie de serveurs](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).  
  
## <a name="feature-summary"></a>Résumé des fonctionnalités

 Configurer un serveur de rapports pour qu'il s'exécute en mode intégré SharePoint fournit les fonctionnalités supplémentaires ci-dessous, qui sont disponibles uniquement lorsque vous déployez un serveur de rapports dans ce mode :  
  
-   Utilisez les fonctionnalités de SharePoint de gestion de documents et de collaboration, y compris les alertes. Un site SharePoint fournit un portail unifié permettant d'accéder à tous les éléments de rapport et de les gérer dans un seul emplacement.  
  
-   Utilisez les autorisations SharePoint et les fournisseurs d'authentification pour contrôler l'accès aux rapports, aux modèles et aux autres éléments.  
  
-   Utilisez les topologies de déploiement SharePoint pour distribuer des rapports via une connexion Internet en dehors du pare-feu. Un serveur de rapports fournit des services de traitement de rapports et de données dans le cadre d'un déploiement SharePoint plus vaste, configuré pour l'accès à Internet.  
  
-   Gérez des rapports, des modèles, des sources de données, des planifications et un historique de rapport dans des pages d'application personnalisées sur un site SharePoint. Vous pouvez définir des propriétés, des planifications et des abonnements, ainsi que créer et gérer un historique de rapport sur un site SharePoint de la même manière que vous les créez et gérez à partir d'autres outils dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Publiez ou téléchargez des rapports, des modèles de rapport, des ressources et des fichiers de sources de données partagées dans une bibliothèque SharePoint, y compris Report Center dans Office SharePoint Server.  
  
     Utilisez le Concepteur de rapports, le Générateur de modèles et le Générateur de rapports pour créer des rapports et des sources de données à publier directement dans une bibliothèque SharePoint. Vous pouvez également utiliser l'action Télécharger sur un site SharePoint pour ajouter des définitions de rapport et des modèles de rapport quelconques dans une bibliothèque SharePoint.  
  
     Comme le serveur de rapports traite les définitions de rapport de la même manière, quel que soit le mode serveur utilisé, les données et la mise en page des rapports ne sont pas affectées par le mode serveur. Tout rapport que vous pouvez exécuter sur un serveur de rapports en mode natif peut être exécuté sur un serveur de rapports configuré pour le mode intégré SharePoint.  
  
-   Abonnez-vous à des rapports et livrez-les dans une bibliothèque SharePoint à l'aide d'une nouvelle extension de remise SharePoint. Vous pouvez également livrer des rapports par courrier électronique ou dans un dossier partagé. Les extensions de remise du serveur de rapports sont utilisées pour livrer les rapports. Vous pouvez créer des abonnements pilotés par les données pour une distribution de rapport à grande échelle à l'aide de données d'abonné interrogées au moment de l'exécution.  
  
-   Un composant WebPart Visionneuse de rapports, vous pouvez ajouter aux pages SharePoint pour afficher un rapport à l’intérieur de votre application web SharePoint. Le composant WebPart inclut la navigation entre les pages, rechercher, imprimer et exporter des fonctions.  
  
-   Programmez un nouveau point de terminaison SOAP pour créer des applications personnalisées qui s'intègrent à un site SharePoint. Vous pouvez également utiliser le fournisseur WMI (Windows Management Instrumentation) mis à jour pour configurer par programmation une instance de serveur de rapports qui s'exécute en mode intégré SharePoint.  
  
-   Rapports de services Microsoft Access en mode connecté.  
  
-   Zones AAM (mappages d'accès de substitution), déploiements exposés à Internet et jetons utilisateur SharePoint pour les listes SharePoint.  
  
## <a name="connected-mode-and-local-mode"></a>En mode connecté et mode local

 La version SQL Server 2008 R2 a introduit un nouveau *mode local* pour consulter des rapports d’un serveur SharePoint 2010 qui inclut le complément Microsoft SQL Server 2008 R2 Reporting Services (ou version ultérieure) pour les produits SharePoint 2010 installés.  
  
-   *En Mode local*: mode Local permet de rapports doit être restitué localement à partir de la bibliothèque de documents SharePoint sans intégration avec un serveur de rapports Reporting Services. Le complément Reporting Services pour les produits SharePoint est requis, mais n’est pas un serveur de rapports Reporting Services. Le complément peut être installé de différentes façons, notamment avec l'Outil de préparation des produits SharePoint 2010. Pour plus d’informations sur le mode local, consultez [en mode Local et rapports en mode connecté dans la visionneuse de rapports](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md) et [où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
-   *Mode connecté*: en mode connecté est pris en charge en intégrant un serveur de rapports Reporting Services dans la batterie de serveurs SharePoint à l’aide de l’Administration centrale de SharePoint. L'intégration à un serveur de rapports permet la création de rapports complète de bout en bout, l'utilisation des fonctionnalités de collaboration de SharePoint 2010 et des fonctionnalités de serveur d'un serveur de rapports notamment : abonnements, instantanés et traitement par le serveur.  
  
## <a name="unsupported-sharepoint-features"></a>Fonctionnalités non prises en charge de sharePoint

 Certaines fonctionnalités SharePoint ne sont pas disponibles en mode intégré. Voici une liste des fonctionnalités SharePoint avec que Reporting Services ne s’intègre pas directement :  
  
-   Service Banque d'informations sécurisé.  
  
-   Vous ne pouvez pas utiliser l'intégration du calendrier Outlook dans SharePoint ni la planification SharePoint pour les fichiers de Reporting Services dans une bibliothèque de documents.  
  
-   Catalogue de données métier SharePoint.  
  
-   Personnalisation SharePoint n’est pas également pris en charge sur les pages de Reporting Services. L'intégration Report Server n'est pas prise en charge si l'application Web SharePoint est activée pour l'accès anonyme.  
  
-   SQL Server Reporting Services ne prend **pas** en charge le contrôle de version de bibliothèque de documents SharePoint. Si vous enregistrez des éléments de rapport dans une bibliothèque de documents pour laquelle l'option Historique des versions du document est activée, les fonctionnalités de Reporting Services ne fonctionnent pas correctement et génèrent des erreurs dans le journal ULS. L'exemple suivant montre une erreur dans le journal ULS :  
  
    -   « …une source de données associée au rapport a été désactivée ».  
  
     L'historique des versions de la bibliothèque de documents est configuré dans la page Paramètres de contrôle de version de Paramètres de la bibliothèque.  
  
## <a name="supported-combinations-of-the-sharepoint-add-in-and-report-server"></a>Combinaisons prises en charge du serveur de rapport et de complément SharePoint

 Certaines fonctionnalités ne sont pas prises en charge dans toutes les combinaisons de serveur de rapports, complément Reporting Services pour SharePoint et produits SharePoint. Pour plus d’informations, consultez [pris en charge les combinaisons de SharePoint et le serveur Reporting Services et compléments](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
> [!NOTE]  
>  La version correcte du complément Reporting Services doit être utilisée avec la version correspondante des produits SharePoint.  
  
## <a name="components-that-provide-integration"></a>Composants qui fournissent l’intégration

 Pour associer les serveurs dans un déploiement unique, vous intégrez une installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Reporting Services avec une instance des produits SharePoint  
  
 L’intégration est fournie par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le complément Reporting Services pour les produits SharePoint. La macro complémentaire Reporting Services est un composant librement distribuable que vous pouvez télécharger et installer sur un serveur qui exécute la version appropriée de SharePoint.  
  
> [!TIP]  
>  Certaines fonctionnalités ne sont pas prises en charge dans toutes les combinaisons de serveur de rapports, complément Reporting Services pour SharePoint et produits SharePoint. Pour plus d’informations, consultez [pris en charge les combinaisons de SharePoint et le serveur Reporting Services et compléments](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   Sur SharePoint, la macro complémentaire Reporting Services fournit le point de terminaison proxy ReportServer, un composant WebPart Visionneuse de rapports et pages d’application afin que vous pouvez afficher, stocker et gérer le contenu du serveur de rapports sur un site SharePoint ou une batterie de serveurs.  
  
-   Dans Reporting Services fournit des extensions de sécurité et de remise personnalisées, un point de terminaison SOAP et les fichiers programme mis à jour. Le serveur de rapports doit être configuré pour s'exécuter en mode intégré SharePoint, dédié exclusivement à la prise en charge de la remise des rapports et de l'accès aux rapports par le biais de votre site SharePoint.  
  
 Après avoir installé la macro complémentaire Reporting Services dans SharePoint et que vous configurez les deux serveurs pour l’intégration, vous pouvez télécharger ou publier des types de contenu de serveur de rapports dans une bibliothèque SharePoint, puis afficher et gérer ces documents à partir d’un site SharePoint. Téléchargement ou de la publication du contenu du serveur de rapports est une première étape importante ; le composant WebPart et les pages deviennent disponibles lorsque vous sélectionnez des définitions de rapport (.rdl), modèles de rapport (.smdl) et sources de données (.rsds) sur un site SharePoint partagées.  
  
##  <a name="language-considerations"></a>Considérations relatives à la langue

 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] et [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] sont disponibles dans beaucoup plus de langues que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Lorsque vous configurez un serveur de rapports pour qu'il s'exécute dans un déploiement d'un produit SharePoint, vous pouvez éventuellement constater une combinaison de langues. L'interface utilisateur, la documentation et les messages apparaissent dans les langues suivantes :  
  
-   Toutes les pages d’application, outils, erreurs, avertissements et les messages qui proviennent de Reporting Services seront affiche dans la langue utilisée par l’instance de Reporting Services dans un de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] langues.  
  
-   Pages d’application que vous ouvrez sur un site SharePoint, le composant WebPart Visionneuse de rapports et le Générateur de rapports seront affiche dans un des langages pris en charge pour la macro complémentaire Reporting Services. Pour afficher la liste des langues prises en charge, accédez à [téléchargements SQL Server](http://msdn.microsoft.com/sql/downloads/) et recherchez la page de téléchargement pour le SQL Server 2016 Reporting Services complément.  
  
-   Les sites SharePoint, l'administration centrale de SharePoint, l'aide en ligne et les messages sont disponibles dans les langues prises en charge par les produits Office Server.  
  
 Si la langue de votre produit ou technologie SharePoint diffère de la langue du serveur de rapports, Reporting Services tente d’utiliser une langue de la même famille de langues qui correspond le mieux. Si aucun substitut proche n'est disponible, le serveur de rapports utilise l'anglais.  
  
## <a name="related-tasks"></a>Tâches associées

 Le tableau suivant récapitule les tâches liées à un serveur de rapports en mode SharePoint de Reporting Services :  
  
|**Tâche**|**Lien**|  
|--------------|--------------|  
|Étapes détaillées pour l’installation et configuration de Reporting Services en mode SharePoint.|[Installer le mode SharePoint de Reporting Services pour SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c) et [ajouter un serveur de rapports supplémentaires à une batterie de serveurs](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).|  
|Montée en puissance votre déploiement SharePoint de Reporting Services en ajoutant des serveurs de rapports supplémentaires.|[Ajouter un serveur de rapports supplémentaires à une batterie de serveurs](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) et [topologies de déploiement pour les fonctionnalités de SQL Server BI dans SharePoint](http://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26).|  
|Ajoutez supplémentaires web frontaux SharePoint qui ont les composants de Reporting Services installés pour les éléments de rapport et d’affichage.|[Ajouter un frontal de web Reporting Services supplémentaire à une batterie de serveurs](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Configurer la messagerie électronique pour votre serveur de rapports dans SharePoint.|[Configurer la messagerie électronique pour une application de service Reporting Services](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|
|Les informations récentes pour cette version s'appuient sur TechNet Wiki.|[Conseils de SQL Server 2012 Reporting Services, astuces et dépannage](http://go.microsoft.com/fwlink/?LinkId=221297).|  

## <a name="next-steps"></a>Étapes suivantes

[Installer ou désinstaller sdd dans Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
[État du composant WebPart Visionneuse de sur un site SharePoint](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
[Quiz : Configuration de SSRS 2012 pour l’intégration SharePoint](http://go.microsoft.com/fwlink/?LinkId=306443)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

