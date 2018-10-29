---
title: Intégration de Reporting Services à l’aide des contrôles Visionneuse de rapports | Microsoft Docs
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
helpviewer_keywords:
- Report Viewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b4b7eb42e3254e92b1b9778ac3866178f68e72f2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786637"
---
# <a name="integrating-reporting-services-using-report-viewer-controls"></a>Intégration de Reporting Services à l’aide des contrôles Visionneuse de rapports
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2015 fournit deux contrôles Visionneuse de rapports permettant d’intégrer des fonctionnalités d’affichage de rapports dans vos applications. Il existe une version pour les applications Windows Forms et une version pour les applications Web Forms. Chaque contrôle offre des fonctionnalités similaires, mais chacun est conçu pour un environnement particulier. Les deux contrôles peuvent traiter des rapports qui ont été déployés sur un serveur de rapports (mode de traitement à distance) ou qui ont été copiés sur un ordinateur où [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n’a pas été installé (mode de traitement local).  
  
 Le contrôle Visionneuse de rapports n'offre pas la prise en charge intégrée de l'adaptation dynamique à différents appareils avec différentes résolutions d'écran.  
  
## <a name="remote-processing-mode"></a>Mode de traitement à distance  
 Le mode de traitement à distance est la méthode recommandée pour consulter les rapports qui ont été déployés sur un serveur de rapports. Le mode de traitement à distance offre les avantages suivants :  
  
-   Le traitement à distance offre une solution optimisée pour l'exécution de rapports car le rapport est traité par le serveur de rapports.  
  
-   Dans la mesure où l'ensemble du traitement est géré par le serveur de rapports, une demande de rapport peut être traitée par plusieurs serveurs de rapports dans un déploiement avec montée en puissance parallèle ou par un serveur doté de plusieurs processeurs dans un déploiement avec montée en puissance par unité.  
  
 Par ailleurs, les rapports exécutés en mode à distance peuvent utiliser l'ensemble des fonctionnalités du serveur de rapports, notamment toutes les extensions de rendu et de données.  
  
> [!NOTE]  
>  La liste des extensions disponibles pour le contrôle Visionneuse de rapports lorsqu'il s'exécute en mode de traitement à distance dépend de l'édition de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui est installée sur le serveur de rapports.  
  
## <a name="local-processing-mode"></a>Mode de traitement local  
 Le mode de traitement local est une autre méthode d'affichage et de rendu des rapports qui peut être utilisée lorsque [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas installé. Contrairement au traitement à distance, seul un sous-ensemble des fonctionnalités fournies par le serveur de rapports est disponible dans le contrôle. En mode de traitement local, le traitement des données n'est pas géré par le contrôle, mais implémenté par l'application hôte. Cependant, le traitement des rapports est géré par le contrôle lui-même. En mode de traitement local, seules les extensions de rendu PDF, Excel, Word et Image sont disponibles.  
  
## <a name="see-also"></a> Voir aussi  
 [Intégration de Reporting Services dans des applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Utilisation du contrôle WebForms Visionneuse de rapports](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [Utilisation du contrôle WinForms Visionneuse de rapports](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  
