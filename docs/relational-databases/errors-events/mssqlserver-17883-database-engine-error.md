---
title: MSSQLSERVER_17883 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6228ef52269a304a5e72a3ff3bc50b915ab372f4
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver17883"></a>MSSQLSERVER_17883
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17883|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SRV_SCHEDULER_NONYIELDING|  
|Texte du message|Le processus %ld:%ld:%ld (0x%lx) travail 0x%p semble être improductif dans le Planificateur %ld. Heure de création du thread : %I64d. Utilisation approximative de l'UC pour ce thread : noyau %I64d ms, utilisateur %I64d ms. Utilisation du processus %d%%. Système inactif %d%%. Intervalle : %I64d ms.|  
  
## <a name="explanation"></a>Explication  
Indique un problème possible avec un thread improductif dans un Planificateur.  Il peut s'agir d'un bogue dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou si le nombre de cycles à exécuter par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est insuffisant.  Cette erreur peut se résoudre si le thread finit par être productif.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Si la charge excessive sur le système réduit la charge en général, contactez le service de support technique Microsoft.  
  

