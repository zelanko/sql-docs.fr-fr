---
title: "Rechercher les serveurs (Serveurs réseau) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0dfaef0364cf72e994b0fe5de778adc8a18bd715
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="browse-for-servers-network-servers"></a>Parcourir les serveurs (Serveurs réseau)
Quand vous vous connectez à un composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sans connaître le nom exact de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], dans la zone **Nom du serveur**, cliquez sur **Parcourir** pour ouvrir la boîte de dialogue **Rechercher les serveurs**.  
  
Cette boîte de dialogue est remplie par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser sur les ordinateurs serveurs. Plusieurs raisons peuvent expliquer pourquoi le nom d'une instance n'apparaît pas dans la liste :  
  
-   Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser ne fonctionne peut-être pas sur l'ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Le port UDP 1434 est peut-être bloqué par un pare-feu.  
  
-   L’indicateur **HideInstance** est peut-être défini.  
  
Pour vous connecter à une instance qui n'apparaît pas dans la liste, entrez une chaîne de connexion complète pour l'instance, y compris le numéro de port TCP/IP ou le nom des canaux nommés.  
  
## <a name="options"></a>Options  
**Sélectionnez une instance de SQL Server sur le réseau pour votre connexion**  
Désignez le serveur auquel vous souhaitez vous connecter en cliquant sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] affichée dans l'arborescence. Vous pouvez afficher ou masquer des parties de l’arborescence en cliquant sur les nœuds identifiés par un symbole **+** ou **–** .  
  

