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
ms.openlocfilehash: 8dd4e6ce7800c3a0a9db51f6c1a4bddfe7a188c3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931690"
---
# <a name="validate-a-sql-server-installation"></a>Valider une installation de SQL Server
  Le rapport de découverte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisé pour vérifier la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur. Le ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rapport de découverte des fonctionnalités installées** affiche un rapport de tous les produits et fonctionnalités de,,,, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] installés sur le serveur local. Le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est disponible sur la page **Outils** du Centre d'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Pour exécuter le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rapport de découverte des fonctionnalités :**  
  
 Lancez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Centre d’installation, à l’aide du menu **Démarrer** , pointez sur **tous les programmes**, ** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name> **sur, sur **outils de configuration**, puis cliquez sur ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Centre d’installation**. Pour exécuter le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cliquez sur **Outils** dans la zone de navigation gauche du **Centre d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** , puis cliquez sur **Rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées**.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rapport de découverte est enregistré dans% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<dernière session d’installation \> .  
  
 Vous pouvez également générer le rapport de découverte via la ligne de commande. Exécutez « Setup.exe/action = RunDiscovery » à partir d’une invite de commandes. Si vous ajoutez « /q » à la ligne de commande ci-dessus, aucune interface utilisateur ne s’affiche, mais le rapport est toujours créé dans% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<dernière session d’installation \> .  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et lire les fichiers journaux d'installation de SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
