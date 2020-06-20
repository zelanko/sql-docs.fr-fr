---
title: Options (page résultats de la requête et services de dépendance) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d19228fdf17788e9118367a6f0f0eb3be90cb72a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930130"
---
# <a name="options-query-results-and-dependency-services-page"></a>Options (Résultats de la requête et Page Services de dépendance)
  Utilisez cette page pour spécifier le serveur auquel se connecter pour les services de dépendance. Les services de dépendance vous permettent d'extraire des informations à propos des dépendances entre des objets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stockés sur des serveurs différents. Vous pouvez afficher les dépendances d’objets à l’aide de la boîte de dialogue **dépendances d’objets** dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] .  
  
 **Que voulez-vous faire ?**  
  
1.  [Ouvrir la boîte de dialogue d'options (Résultats de la requête/page Services de dépendance)](#open_dialog)  
  
2.  [Configurer les options](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a>Ouvrir la boîte de dialogue Options (résultats de la requête/page services de dépendance)  
  
1.  Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , cliquez sur **options** dans le menu **Outils** .  
  
2.  Développez **Résultats de la requête**, puis cliquez sur **Services de dépendance**.  
  
##  <a name="configure-the-options"></a><a name="options"></a>Configurer les options  
  
### <a name="options"></a>Options  
 **Serveur de services de dépendance**  
 Spécifiez le serveur sur lequel les services de dépendance sont installés.  
  
 **Authentification**  
 Sélectionnez l'authentification Windows pour vous connecter à l'aide d'un compte d'utilisateur Microsoft Windows ou sélectionnez l'authentification SQL Server.  
  
 Lorsqu'un utilisateur se connecte avec un nom d'accès et un mot de passe spécifiés à partir d'une connexion non autorisée, SQL Server réalise l'authentification en vérifiant si un compte de connexion SQL Server a été défini et si le mot de passe spécifié correspond à celui enregistré précédemment. Si SQL Server ne peut pas trouver le compte de connexion, l'authentification échoue et l'utilisateur reçoit un message d'erreur.  
  
 **Nom d'utilisateur**  
 Si vous utilisez l'authentification SQL Server, entrez un nom d'utilisateur.  
  
 **Mot de passe**  
 Si vous utilisez l'authentification SQL Server, entrez un mot de passe.  
  
 **Test**  
 Cliquez pour vérifier la connexion.