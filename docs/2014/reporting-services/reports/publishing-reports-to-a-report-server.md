---
title: Publication de rapports sur un serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5c73e75bbdf458b27d0f879a91e72ececc832b88
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102491"
---
# <a name="publishing-reports-to-a-report-server"></a>Publication de rapports sur un serveur de rapports
  Après avoir conçu et testé un rapport ou un ensemble de rapports, vous pouvez utiliser les fonctionnalités de déploiement intégrées dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour publier les rapports sur un serveur de rapports. Vous pouvez publier des rapports individuels ou un projet Report Server. La publication d'un projet Report Server est la méthode la plus simple pour publier plusieurs rapports. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]utilise le terme *déployer*, au lieu du terme *publier*. Les deux termes sont interchangeables.  
  
 Avant de publier un rapport, vous devez bénéficier de l'autorisation de le faire. L'autorisation est déterminée via la sécurité basée sur les rôles définie par votre administrateur du serveur de rapports. Les opérations de publication sont généralement autorisées par le biais du rôle Serveur de publication.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] fournit des configurations de projet pour la gestion de la publication de rapports. La configuration spécifie l'emplacement du serveur de rapports, la version de SQL Server Reporting Services installée sur le serveur de rapports, si les sources de données publiées sur le serveur de rapports sont remplacées, etc. Outre les configurations fournies par [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , vous pouvez créer des configurations supplémentaires.  
  
## <a name="project-configurations"></a>Configurations de projet  
 Les rapports sont générés avant d'être publiés pour garantir que seules les définitions de rapports valides sont publiées sur le serveur de rapports. Les configurations de projet incluent des propriétés pour la génération de rapports, telles que le dossier dans lequel les rapports créés doivent être stockés temporairement, et le mode de gestion des problèmes de génération. Les configurations ont également des propriétés que vous utilisez pour spécifier l'emplacement et la version du serveur de rapports, les dossiers sur le serveur de rapports.  
  
 Par défaut, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] fournit trois configurations de projet : DebugLocal, Debug et Release. La configuration par défaut est DebugLocal. Vous utilisez en général la configuration DebugLocal pour afficher un aperçu des rapports dans une fenêtre d’aperçu locale, la configuration Debug pour publier des rapports sur un serveur de test et la configuration Release pour publier des rapports sur un serveur de production. La liste déroulante des configurations de solution dans la barre d'outils Standard affiche la configuration active. Pour utiliser une configuration différente, sélectionnez-la dans la liste.  
  
 Plusieurs serveurs de rapports et versions différentes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent être installés dans votre environnement de création de rapports. Vous pouvez créer plusieurs configurations, puis en utiliser une différente selon le scénario de déploiement. Pour plus d’informations, consultez [déploiement et prise en charge des versions dans SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) et [définir des propriétés de déploiement &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md).  
  
## <a name="publishing-reports"></a>Publication de rapports  
 Vous pouvez publier un rapport unique ou un projet Report Server qui contient plusieurs rapports. Pour obtenir des instructions sur la publication de rapports, consultez [publier des rapports](../publish-reports.md).  
  
### <a name="publishing-a-single-report"></a>Publication d'un seul rapport  
 Si vous ne souhaitez pas publier tous les rapports d'un projet, vous pouvez choisir de n'en publier qu'un seul. Pour cela, sélectionnez une configuration qui déploie le rapport (par exemple, Release), cliquez avec le bouton droit sur ce rapport, puis cliquez sur **Déployer**.  
  
 Si un rapport utilise une source de données partagée, vous devez également la déployer ou le rapport déployé ne s'exécutera pas. Cliquez avec le bouton droit sur la source de données partagée, puis cliquez sur **Déployer**.  
  
 L'URL de serveur cible du serveur de rapports doit être spécifiée et vous pouvez modifier les dossiers par défaut vers lesquels les rapports et sources de données partagées sont déployés.  
  
### <a name="publishing-multiple-reports"></a>Publication de plusieurs rapports  
 Lorsque vous publiez un projet Report Server, vous publiez tous les rapports de ce projet. Tous les rapports sont déployés à l'aide de la même configuration de projet : sur le même serveur de rapports, le même dossier sur le serveur, et ainsi de suite. Pour publier des rapports sur différents serveurs, publiez-les un par un ou incluez uniquement les rapports que vous souhaitez dans le projet Report Server. Une solution peut inclure plusieurs projets Report Server et l'utilisation de plusieurs projets peut simplifier la gestion du déploiement des rapports, car vous pouvez utiliser une configuration différente pour déployer des projets différents.  
  
## <a name="see-also"></a>Voir aussi  
 [Pages de propriétés du projet, boîte de dialogue](../tools/project-property-pages-dialog-box.md)   
 [Gestion du contenu du serveur de rapports &#40;SSRS en mode natif&#41;](../report-server/report-server-content-management-ssrs-native-mode.md)   
 [Rapports de mise à niveau](../install-windows/upgrade-reports.md)  
  
  
