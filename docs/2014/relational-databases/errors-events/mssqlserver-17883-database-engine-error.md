---
title: MSSQLSERVER_17883 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2f9f712ed8d37872c90eff773e81a657fb96c296
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62915268"
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
  
  
