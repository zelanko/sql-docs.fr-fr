---
title: Options (résultats de la requête et de la Page Services de dépendance) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: mashamsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f587ee792809f9612ca9fca1264794e843172a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118619"
---
# <a name="options-query-results-and-dependency-services-page"></a>Options (Résultats de la requête et Page Services de dépendance)
  Utilisez cette page pour spécifier le serveur auquel se connecter pour les services de dépendance. Les services de dépendance vous permettent d'extraire des informations à propos des dépendances entre des objets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stockés sur des serveurs différents. Afficher les dépendances d’objets à l’aide de la **dépendances d’objets** boîte de dialogue dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 **Que voulez-vous faire ?**  
  
1.  [Ouvrez la boîte de dialogue Options (Page de requête résultats/dépendance Services)](#open_dialog)  
  
2.  [Configurer les options](#options)  
  
##  <a name="open_dialog"></a> Ouvrez la boîte de dialogue Options (Page de requête résultats/dépendance Services)  
  
1.  Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], cliquez sur **Options** sur le **outils** menu.  
  
2.  Développez **Résultats de la requête**, puis cliquez sur **Services de dépendance**.  
  
##  <a name="options"></a> Configurer les options  
  
### <a name="options"></a>Options  
 **Serveur de Services de dépendance**  
 Spécifiez le serveur sur lequel les services de dépendance sont installés.  
  
 **Authentification**  
 Sélectionnez l'authentification Windows pour vous connecter à l'aide d'un compte d'utilisateur Microsoft Windows ou sélectionnez l'authentification SQL Server.  
  
 Lorsqu'un utilisateur se connecte avec un nom d'accès et un mot de passe spécifiés à partir d'une connexion non autorisée, SQL Server réalise l'authentification en vérifiant si un compte de connexion SQL Server a été défini et si le mot de passe spécifié correspond à celui enregistré précédemment. Si SQL Server ne peut pas trouver le compte de connexion, l'authentification échoue et l'utilisateur reçoit un message d'erreur.  
  
 **Nom d'utilisateur**  
 Si vous utilisez l'authentification SQL Server, entrez un nom d'utilisateur.  
  
 **Mot de passe**  
 Si vous utilisez l'authentification SQL Server, entrez un mot de passe.  
  
 **Tester**  
 Cliquez pour vérifier la connexion.  
  
  
