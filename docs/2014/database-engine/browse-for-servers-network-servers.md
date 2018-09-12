---
title: Rechercher les serveurs (Serveurs réseau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 27
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a43e1efc508195b837879305080c7eb6636a2141
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43811625"
---
# <a name="browse-for-servers-network-servers"></a>Parcourir les serveurs (Serveurs réseau)
  Quand vous vous connectez à un composant [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sans connaître le nom exact de l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], dans la zone **Nom du serveur**, cliquez sur **Parcourir** pour ouvrir la boîte de dialogue **Rechercher les serveurs**.  
  
 Cette boîte de dialogue est remplie par le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser sur les ordinateurs serveurs. Plusieurs raisons peuvent expliquer pourquoi le nom d'une instance n'apparaît pas dans la liste :  
  
-   Le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser ne fonctionne peut-être pas sur l'ordinateur qui exécute [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Le port UDP 1434 est peut-être bloqué par un pare-feu.  
  
-   L’indicateur **HideInstance** est peut-être défini.  
  
 Pour vous connecter à une instance qui n'apparaît pas dans la liste, entrez une chaîne de connexion complète pour l'instance, y compris le numéro de port TCP/IP ou le nom des canaux nommés.  
  
## <a name="options"></a>Options  
 **Sélectionnez une instance de SQL Server sur le réseau pour votre connexion**  
 Désignez le serveur auquel vous souhaitez vous connecter en cliquant sur l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] affichée dans l'arborescence. Vous pouvez afficher ou masquer des parties de l’arborescence en cliquant sur les nœuds identifiés par un symbole **+** ou **–** .  
  
  
