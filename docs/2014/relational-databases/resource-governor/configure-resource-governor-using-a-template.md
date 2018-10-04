---
title: Configurer Resource Governor à l’aide d’un modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2eb72f7eabd9bb265adba697264942e9b4fdf400
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096079"
---
# <a name="configure-resource-governor-using-a-template"></a>Configurer Resource Governor à l'aide d'un modèle
  Vous pouvez configurer Resource Governor à l'aide d'un modèle fourni dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Before you begin:**  [Permissions](#Permissions)  
  
-   **Pour créer un groupe de charge de travail, avec :**  [un modèle](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Utilisez les étapes suivantes pour ouvrir et modifier un modèle qui crée un pool de ressources et un groupe de charge de travail pour le pool. De plus, ce modèle vous permet de créer une fonction classifieur définie par l'utilisateur qui achemine de nouvelles connexions vers le groupe par défaut ou le groupe de charge de travail que vous créez.  
  
###  <a name="Permissions"></a> Permissions  
 Les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] de Resource Governor dans le modèle requièrent l'autorisation CONTROL SERVER.  
  
##  <a name="ConfRGTemplate"></a> Configurer Resource Governor à l'aide d'un modèle  
 **Pour configurer Resource Governor à l'aide d'un modèle dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans le menu **Affichage** , cliquez sur **Explorateur de modèles**.  
  
2.  Dans **Explorateur de modèles**, développez **Resource Governor**, puis double-cliquez sur **Configurer Resource Governor**.  
  
3.  Dans **Se connecter au moteur de base de données**, entrez les informations requises, puis cliquez sur **OK**. Le modèle Configure Ressource Governor.sql est fourni dans l'Éditeur de requête. Utilisez ce modèle pour créer et configurer un pool de ressources, un groupe de charges de travail et une fonction classifieur.  
  
4.  Pour modifier les valeurs dans le modèle, appuyez sur CTRL+Maj+M. Dans la fenêtre **Spécifier les valeurs des paramètres du modèle** , entrez les valeurs de votre choix.  
  
5.  Pour enregistrer les modifications que vous apportez au modèle, cliquez sur **OK**.  
  
6.  Pour exécuter la requête, cliquez sur **Exécuter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Activer Resource Governor](enable-resource-governor.md)   
 [Pool de ressources de Resource Governor](resource-governor-resource-pool.md)   
 [Groupe de charge de travail de Resource Governor](resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](resource-governor-classifier-function.md)   
 [Afficher les propriétés de Resource Governor](view-resource-governor-properties.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
