---
title: Créer un rôle défini par l’utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8405be955cdfd4f0d8b9665665f8817c98b9d60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153065"
---
# <a name="create-a-user-defined-role"></a>Créer un rôle défini par l'utilisateur
    
### <a name="to-create-a-user-defined-role"></a>Pour créer un rôle défini par l'utilisateur  
  
1.  Ouvrir [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Cliquez sur **Explorateur d'objets** dans le menu **Affichage** .  
  
3.  Dans la barre d'outils de l'Explorateur d'objets, cliquez sur **Connecter**, puis sur **Moteur de base de données**.  
  
4.  Dans la boîte de dialogue **Se connecter au serveur** , entrez un nom de serveur et sélectionnez un mode d'authentification. Vous pouvez utiliser un point (.), (local), ou `localhost` pour indiquer le serveur local.  
  
5.  Cliquez sur **Se connecter**.  
  
6.  Développez Bases de données, Bases de données système, msdb, Sécurité et Rôles.  
  
7.  Dans le nœud Rôles, cliquez avec le bouton droit sur Rôles de base de données, puis cliquez sur **Nouveau rôle de base de données**.  
  
8.  Sur la page Général, entrez un nom, et, si vous le souhaitez, spécifiez un propriétaire et des schémas appartenant à un rôle et ajoutez des membres de rôle.  
  
9. Vous pouvez également cliquer sur **Autorisations** pour configurer les autorisations pour les objets.  
  
10. Vous pouvez également cliquer sur **Propriétés étendues** pour configurer les éventuelles propriétés étendues.  
  
11. Cliquez sur **OK**.  
  
  