---
title: Activer la fonctionnalité d’intégration PowerPivot pour les Collections de sites dans l’Administration centrale | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 00e8f0336c075c14feb8c4e3b4a8b43e0ebdaf9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141900"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>Activer la fonctionnalité d'intégration PowerPivot pour des collections de sites dans l'Administration centrale
  Activer la fonctionnalité d'intégration PowerPivot pour des collections de sites spécifiques est indispensable si vous avez utilisé l'option d'installation Batterie de serveurs existante lors de l'installation de SQL Server PowerPivot pour SharePoint. Si vous avez installé PowerPivot pour SharePoint à l'aide de l'option Nouveau serveur, vous pouvez ignorer cette tâche, car le programme d'installation de SQL Server a déjà activé la fonctionnalité d'intégration PowerPivot pour la collection de sites racine lorsqu'il a configuré votre déploiement.  
  
 L'activation de fonctionnalités au niveau de la collection de sites est nécessaire pour mettre à disposition de vos sites des pages et des modèles d'application, notamment des pages de configuration pour l'actualisation des données planifiée et des pages d'application pour la bibliothèque Galerie PowerPivot et les bibliothèques de flux.  
  
 Vous devez activer l'intégration de PowerPivot pour chaque collection de sites qui prend en charge le traitement des requêtes PowerPivot.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez être administrateur de collection de sites.  
  
## <a name="activate-powerpivot-features"></a>Activer les fonctionnalités PowerPivot  
  
1.  Sur un site SharePoint, cliquez sur **Actions du site**.  
  
     Par défaut, les applications Web SharePoint sont accessibles via le port 80. Cela signifie que vous pouvez souvent accéder à un site SharePoint en entrant http://\<nom de l’ordinateur > pour ouvrir la collection de sites racine.  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Dans Administration de la collection de sites, cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Faites défiler vers le bas de la page jusqu'à ce que vous trouviez **fonctionnalité de Collection de sites PowerPivot Integration**.  
  
5.  Cliquez sur **Activer**.  
  
6.  Répétez ces étapes pour les collections de sites supplémentaires en ouvrant chaque site et en cliquant sur **Actions du site**.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de serveur PowerPivot et de Configuration dans l’Administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configuration initiale &#40;PowerPivot pour SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [Installation PowerPivot pour SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  