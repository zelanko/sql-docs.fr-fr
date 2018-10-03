---
title: Mettre à niveau tous les serveurs cibles avant la mise à niveau le serveur maître | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97272209c1ceba780711ecf4a07178ddf8943d49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061943"
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
  
  
