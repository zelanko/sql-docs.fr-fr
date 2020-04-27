---
title: Modifications du comportement des indicateurs de trace | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 447e6d4d35fa77f71f1a7a1b90a5a782e0ccebcc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096622"
---
# <a name="changes-to-behavior-of-trace-flags"></a>Modifications du comportement des indicateurs de trace
  Les indicateurs de trace globaux définis par une session prennent effet dans d'autres sessions immédiatement. Certains indicateurs de trace de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] n'existent plus dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Nous vous conseillons de désactiver tous les indicateurs de trace avant d'effectuer la mise à niveau. Les indicateurs de trace qui modifient la disponibilité de la base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] données ou les modes de récupération peuvent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]empêcher le de mettre à niveau votre instance de. Vous pouvez activer les indicateurs de trace après avoir vérifié que les indicateurs de trace sont requis et encore valides dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Si vous devez réactiver des indicateurs de trace, vous devez effectuer des tests supplémentaires sur votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge les indicateurs de trace globaux et de niveau session. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les indicateurs de trace peuvent être spécifiés comme locaux ou globaux à l'aide d'un argument supplémentaire (-1) dans la commande DBCC TRACEON. Si cet argument n'est pas spécifié, les indicateurs sont locaux par défaut.  
  
 En outre, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]dans, un indicateur de trace défini dans la session a ne prend pas automatiquement effet dans une session B existante. Au lieu de cela, cet indicateur de trace prend effet uniquement après la première fois qu’un indicateur de trace est défini dans la session B. Ce comportement n’est pas déterministe [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] dans et est déterministe [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] dans et les versions ultérieures, où les indicateurs de trace globaux définis dans la session A sont définis immédiatement dans d’autres sessions simultanées.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
