---
title: Mettre à niveau tous les serveurs cibles avant la mise à niveau le serveur maître | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d0df73fdfa1ebbaa84b0fb11519698351a78ffdc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218669"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>Mettre à niveau tous les serveurs cibles avant de mettre à niveau le serveur maître
  Avant de mettre à niveau le serveur maître, mettez à niveau tous les ordinateurs exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et configurés comme serveurs cibles.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Pour automatiser l'administration dans des environnements multiserveurs, vous devez disposer, au minimum, d'un serveur maître et d'un serveur cible. Un serveur maître distribue les travaux aux serveurs cibles et reçoit les événements de ces derniers. Un serveur maître stocke également la copie centrale des définitions de travaux pour les travaux exécutés sur des serveurs cibles.  
  
 Si le serveur actif est configuré en tant que serveur maître, mettez à niveau tous les serveurs cibles avant de mettre à niveau le serveur maître.  
  
## <a name="corrective-action"></a>Action corrective  
 Si vous ne pouvez pas mettre à niveau tous les serveurs cibles avant de mettre à niveau le serveur maître, vous devez désinscrire tous les serveurs cibles et les réinscrire après la mise à niveau.  
  
 Pour plus d'informations, consultez les rubriques « Automatisation de l'administration à l'échelle d'une entreprise », « Procédure : désinscrire un serveur cible d'un serveur maître » et « Procédure : inscrire un serveur cible sur un serveur maître » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [Problèmes de mise à niveau de SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
