---
title: Rechercher les serveurs (Serveurs réseau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ffa52839c20a34574423e3b123da79f734fb69ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786685"
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
 Désignez le serveur auquel vous souhaitez vous connecter en cliquant sur l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] affichée dans l'arborescence. Vous pouvez afficher ou masquer des parties de l’arborescence en cliquant sur les nœuds identifiés par un **+** ou **-** symbole.  
  
  
