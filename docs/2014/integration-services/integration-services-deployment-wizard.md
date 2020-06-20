---
title: Assistant Déploiement de Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 727eb2b745a732049d6eb4a5e2f1808f076167d0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968307"
---
# <a name="integration-services-deployment-wizard"></a>Assistant Déploiement d’Integration Services
  L'Assistant Déploiement d'[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] déploie des projets dans le catalogue SSISDB sur une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide du modèle de déploiement de projet.  
  
 Pour démarrer l' [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Assistant déploiement à partir d’un projet ouvert dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , sélectionnez **déployer** dans le menu **projet** . Pour démarrer l’Assistant dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , développez le nœud **Integration Services catalogues**  >  **SSISDB** dans l’Explorateur d’objets, cliquez avec le bouton droit sur le dossier **projets** , puis cliquez sur **déployer le projet**.  
  
 L'Assistant effectue les quatre étapes ci-après. Cliquez sur **suivant** pour passer à l’étape suivante, ou sur **précédent** pour revenir à l’étape précédente.  
  
1.  **Sélectionnez source** -sélectionnez le [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projet que vous souhaitez déployer.  
  
2.  **Sélectionner** la destination : sélectionnez la destination du projet.  
  
3.  **Consulter** : affiche vos sélections.  
  
4.  **Déployer/résultats** -déploie le projet et affiche les résultats.  
  
## <a name="select-source"></a>Sélectionner la source  
 Pour déployer un fichier de déploiement de projet que vous avez créé, sélectionnez **fichier de déploiement de projet** , puis entrez le chemin d’accès au fichier. ISPAC ou cliquez sur **Parcourir** pour le trouver dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dossier du projet. Pour déployer un projet qui réside dans le catalogue [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , sélectionnez **Catalogue Integration Services**, puis entrez le nom du serveur et le chemin d'accès au projet au sein du catalogue.  
  
 Si vous démarrez l'Assistant dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], l'Assistant sélectionne ensuite par défaut le projet ouvert en tant que source et ignore cette étape. Pour revenir à cette étape et sélectionner une autre source, cliquez sur **précédent** ou sur **Sélectionner une source** dans le volet gauche.  
  
## <a name="select-destination"></a>Sélectionner la destination  
 Pour sélectionner le dossier de destination du projet dans le catalogue [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , entrez l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou cliquez sur **Parcourir** pour sélectionner un serveur dans une liste de serveurs. Entrez le chemin d'accès au projet dans SSISDB ou cliquez sur **Parcourir** pour le sélectionner.  
  
 Si vous démarrez l'Assistant dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], l'Assistant sélectionne ensuite par défaut l'instance de serveur connectée et entre le chemin d'accès du projet sélectionné. Vous pouvez modifier ces valeurs pour déployer le projet dans un autre emplacement.  
  
## <a name="review"></a>Révision  
 L'Assistant vous permet de vérifier les paramètres que vous avez sélectionnés avant de déployer le projet. Vous pouvez modifier vos sélections en cliquant sur **Précédent**ou en cliquant sur l'une des étapes dans le volet gauche.  
  
## <a name="deployresults"></a>Déployer/Résultats  
 Lorsque vous cliquez sur **déployer** à partir de la page **vérifier** , le projet est déployé et la page **résultats** affiche la réussite ou l’échec de chaque action. Si l'action échoue, cliquez sur **Échec** dans la colonne **Résultat** pour afficher une explication de l'erreur. Cliquez sur **enregistrer le rapport...** pour enregistrer les résultats dans un fichier XML.  
  
 Cliquez sur **Fermer** pour quitter l’Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des projets sur Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Déploiement de projets et de packages](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
