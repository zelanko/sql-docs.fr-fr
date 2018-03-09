---
title: "Activer l’intégration de Power Pivot pour des Collections de sites dans l’autorité de certification | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 52fb43ddd40e432cb174c9d0794a3919fc48ff7a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>Activer l’intégration de Power Pivot pour des Collections de sites dans l’autorité de certification
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
L’activation de l’intégration des fonctionnalités [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour des collections de sites spécifiques est indispensable si vous avez utilisé l’option d’installation Batterie de serveurs existante lors de l’installation de SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint. Si vous avez installé [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint à l’aide de l’option Nouveau serveur, vous pouvez ignorer cette tâche, car le programme d’installation de SQL Server a déjà activé l’intégration des fonctionnalités [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour la collection de sites racine lorsqu’il a configuré votre déploiement.  
  
 L’activation des fonctionnalités au niveau de la collection de sites est nécessaire pour mettre à disposition de vos sites des pages et des modèles d’application, notamment des pages de configuration pour l’actualisation de données planifiée et des pages d’application pour la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et les bibliothèques de flux de données.  
  
 Vous devez activer l’intégration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour chaque collection de sites prenant en charge le traitement des requêtes [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="prerequisites"></a>Configuration requise  
 Vous devez être administrateur de collection de sites.  
  
## <a name="activate-power-pivot-features"></a>Activer les fonctionnalités Power Pivot  
  
1.  Sur un site SharePoint, cliquez sur **Actions du site**.  
  
     Par défaut, les applications Web SharePoint sont accessibles via le port 80. Cela signifie que vous pouvez souvent accéder à un site SharePoint en entrant http://\<nom de l’ordinateur > pour ouvrir la collection de sites racine.  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Dans Administration de la collection de sites, cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Faites défiler la page vers le bas jusqu’à ce que vous trouviez **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour les collections de sites**.  
  
5.  Cliquez sur **Activer**.  
  
6.  Répétez ces étapes pour les collections de sites supplémentaires en ouvrant chaque site et en cliquant sur **Actions du site**.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration et configuration d’un serveur Power Pivot dans l’Administration centrale](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configuration initiale (PowerPivot pour SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Installation de PowerPivot pour SharePoint 2010](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  
