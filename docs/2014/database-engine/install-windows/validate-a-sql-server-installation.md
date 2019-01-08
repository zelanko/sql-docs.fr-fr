---
title: Valider une installation de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34e4c29cb28f76c930f1f04152528ca1a8a89dfc
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52415690"
---
# <a name="validate-a-sql-server-installation"></a>Valider une installation de SQL Server
  Le rapport de découverte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisé pour vérifier la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur. Le **installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rapport de découverte des fonctionnalités** affiche un rapport de tous les [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], et [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] produits et des fonctionnalités offertes par sont installés sur le serveur local. Le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est disponible sur la page **Outils** du Centre d'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Pour exécuter le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :**  
  
 Lancez le Centre d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en utilisant le menu **Démarrer**, en pointant sur **Tous les programmes**, en pointant sur **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<nom_version>**, en pointant sur **Outils de configuration**, puis en cliquant sur **Centre d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**. Pour exécuter le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cliquez sur **Outils** dans la zone de navigation gauche du **Centre d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**, puis cliquez sur **Rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées**.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rapport de découverte est enregistré dans %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< dernière Session d’installation\>.  
  
 Vous pouvez également générer le rapport de découverte via la ligne de commande. Exécutez « Setup.exe/action = RunDiscovery » à partir d’une invite de commandes si vous ajoutez « / q » à la ligne de commande ci-dessus aucune interface utilisateur ne s’affiche, mais le rapport est toujours être créé dans % ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< dernière Session d’installation\>.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et lire les fichiers journaux d’installation de SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
