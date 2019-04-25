---
title: Réparer une Installation de Distributed Replay | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d14b1bf3200802e9fab359ba3ede9fa295911fe1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760937"
---
# <a name="repair-a-distributed-replay-installation"></a>Réparer une installation de Distributed Replay
  La réparation d'un composant Distributed Replay (contrôleur ou client) effectuera les opérations suivantes :  
  
1.  Installation de tous les fichiers associés sur le disque et remplacement de tous les fichiers existants.  
  
2.  recréation du compte de service Windows si le compte de service correspondant a été supprimé.  
  
 Vous ne pouvez pas utiliser l'opération de Réparation pour ajouter ou supprimer des composants. Pour ajouter ou supprimer des composants, activez ou désactivez le composant correspondant dans l'arborescence des fonctionnalités sur la page **Sélection de fonctionnalités** dans le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>Pour réparer une installation défaillante de Distributed Replay  
  
1.  Depuis le menu **Démarrer** , cliquez sur **Panneau de configuration**, puis double-cliquez sur **Ajouter ou supprimer des programmes**.  
  
2.  Sélectionnez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans la fenêtre **Désinstaller ou modifier un programme** , puis dans la boîte de dialogue [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , cliquez sur **Réparation**.  
  
3.  Suivez les étapes de l'Assistant [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , et sur la page **Sélection de fonctionnalités** , sélectionnez les composants de Distributed Replay que vous souhaitez réparer, puis cliquez sur **Suivant**.  
  
4.  Complétez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour réparer les fonctionnalités Distributed Replay sélectionnées.  
  
  
