---
title: Activer l’intégration des fonctionnalités PowerPivot pour les collections de sites dans l’administration centrale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b479564984727e47432754d0a660e6aa979244b3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547631"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>Activer la fonctionnalité d'intégration PowerPivot pour des collections de sites dans l'Administration centrale
  Activer la fonctionnalité d'intégration PowerPivot pour des collections de sites spécifiques est indispensable si vous avez utilisé l'option d'installation Batterie de serveurs existante lors de l'installation de SQL Server PowerPivot pour SharePoint. Si vous avez installé PowerPivot pour SharePoint à l'aide de l'option Nouveau serveur, vous pouvez ignorer cette tâche, car le programme d'installation de SQL Server a déjà activé la fonctionnalité d'intégration PowerPivot pour la collection de sites racine lorsqu'il a configuré votre déploiement.  
  
 L'activation de fonctionnalités au niveau de la collection de sites est nécessaire pour mettre à disposition de vos sites des pages et des modèles d'application, notamment des pages de configuration pour l'actualisation des données planifiée et des pages d'application pour la bibliothèque Galerie PowerPivot et les bibliothèques de flux.  
  
 Vous devez activer l'intégration de PowerPivot pour chaque collection de sites qui prend en charge le traitement des requêtes PowerPivot.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez être administrateur de collection de sites.  
  
## <a name="activate-powerpivot-features"></a>Activer les fonctionnalités PowerPivot  
  
1.  Sur un site SharePoint, cliquez sur **Actions du site**.  
  
     Par défaut, les applications Web SharePoint sont accessibles via le port 80. Cela signifie que vous pouvez souvent accéder à un site SharePoint en entrant http://\<computer name> pour ouvrir la collection de sites racine.  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Dans Administration de la collection de sites, cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Faites défiler la page jusqu’à ce que vous trouviez la **fonctionnalité de collection de sites d’intégration PowerPivot**.  
  
5.  Cliquez sur **Activer**.  
  
6.  Répétez ces étapes pour les collections de sites supplémentaires en ouvrant chaque site et en cliquant sur **Actions du site**.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration et configuration du serveur PowerPivot dans l’administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configuration initiale &#40;PowerPivot pour SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
