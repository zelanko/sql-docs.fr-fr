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
ms.openlocfilehash: 0ba5e4e5dd6d9a6541a98e0cb30229d7335bac24
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936080"
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
 Désignez le serveur auquel vous souhaitez vous connecter en cliquant sur l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] affichée dans l'arborescence. Vous pouvez afficher ou masquer des parties de l’arborescence en cliquant sur les nœuds marqués avec **+** un **-** symbole ou.  
  
  
