---
title: Intégration de Reporting Services à des applications | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 33b628894376a909de5ee39b9de5a6e979a679f3
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56036070"
---
# <a name="integrating-reporting-services-into-applications"></a>Intégration de Reporting Services dans les applications
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est une plate-forme de création de rapports ouverte et extensible conçue pour fournir aux développeurs un jeu complet d'API  pour développer des solutions.  
  
 Il existe trois options d’intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à des applications personnalisées : le service Web Report Server, également appelé API SOAP de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les contrôles ReportViewer pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] et l’accès URL. Chaque option représente une approche différente de l'intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications.  
  
## <a name="report-server-web-service"></a>service Web Report Server  
 Le service Web Report Server constitue la principale interface de développement avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Que vous développiez du code pour gérer votre catalogue de rapports ou pour effectuer le rendu de rapports dans un format pris en charge, le service Web propose toutes les méthodes nécessaires pour intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications. Ainsi, par exemple, le Gestionnaire de rapports, qui est inclus dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], utilise le service web pour gérer la base de données du serveur de rapports.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Contrôles ReportViewer pour Visual Studio  
 Les contrôles ReportViewer inclus dans [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] sont utilisés pour intégrer la consultation de rapports dans vos applications. Il existe deux contrôles : un pour les applications Windows Forms et un autre pour les applications Web Forms. Chaque contrôle propose une fonctionnalité de consultation des rapports qui ont été déployés sur un serveur de rapports et permet d'effectuer le rendu de rapports dans un environnement où un aucun serveur de rapports n'est installé.  
  
## <a name="url-access"></a>Accès URL  
 L'accès URL est une autre option d'intégration de la consultation de rapports dans vos applications si les contrôles ReportViewer ne sont pas proposés en option. Par ailleurs, l'accès URL est utile pour envoyer aux utilisateurs des liens vers des rapports par courrier électronique.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Intégration de Reporting Services à l'aide de SOAP](../application-integration/integrating-reporting-services-using-soap.md)  
 Décrit comment intégrer la navigation et la gestion des rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion existantes à l'aide du service Web Report Server.  
  
 [Intégration de Reporting Services à l’aide des contrôles ReportViewer](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Décrit comment intégrer la consultation de rapports dans vos applications existantes à l'aide de contrôles ReportViewer.  
  
 [Intégration de Reporting Services à l'aide de l'accès URL](../application-integration/integrating-reporting-services-using-url-access.md)  
 Décrit comment intégrer la navigation entre les rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion existantes à l'aide de l'accès URL.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Choix entre l’accès URL et SOAP](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md)   
 [Service Web des serveurs de rapports](../report-server-web-service/report-server-web-service.md)  
  
  
