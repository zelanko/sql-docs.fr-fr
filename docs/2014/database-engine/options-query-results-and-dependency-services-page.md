---
title: Options (résultats de la requête et de la Page Services de dépendance) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6f5cabf63916602f3a269b24b1e43e24e42f9082
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039571"
---
# <a name="options-query-results-and-dependency-services-page"></a>Options (résultats de la requête et de la Page Services de dépendance)
  Utilisez cette page pour spécifier le serveur auquel se connecter pour les services de dépendance. Les services de dépendance vous permettent d'extraire des informations à propos des dépendances entre des objets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stockés sur des serveurs différents. Afficher les dépendances d’objets à l’aide de la **dépendances d’objet** boîte de dialogue de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 **Que voulez-vous faire ?**  
  
1.  [Ouvrez la boîte de dialogue Options (Page de requête résultats/dépendance Services)](#open_dialog)  
  
2.  [Configurer les options](#options)  
  
##  <a name="open_dialog"></a> Ouvrez la boîte de dialogue Options (Page de requête résultats/dépendance Services)  
  
1.  Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], cliquez sur **Options** sur la **outils** menu.  
  
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
  
  