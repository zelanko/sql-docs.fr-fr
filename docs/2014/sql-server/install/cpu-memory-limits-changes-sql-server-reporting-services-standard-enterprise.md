---
title: Modifications des limites de processeur et mémoire pour SQL Server Reporting Services Standard et Enterprise | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c6e7f635d945f268b9d39aa1bc219aa38ba6f83c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190309"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>Modifications des limites affectant les processeurs et la mémoire pour SQL Server Reporting Services Standard et Enterprise
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services Standard et Enterprise prennent en charge jusqu'à 64 gigaoctets de mémoire système.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>Description  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Reporting Services Standard et Enterprise prennent en charge jusqu'à 64 gigaoctets de mémoire système. Vous devrez peut-être reconfigurer les paramètres actuels de votre système pour les aligner sur les nouvelles limites.  
  
 Pour plus d’informations sur les limites de processeur et de mémoire pour les autres éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), et [mémoire prise en charge par les éditions de SQL Server](http://go.microsoft.com/fwlink/?LinkId=212633).  
  
## <a name="corrective-action"></a>Action corrective  
 Vous devrez peut-être reconfigurer les paramètres actuels de votre système pour les aligner sur les nouvelles limites du processeur et de la mémoire. Pour plus d’informations, consultez [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), et [Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Compatibilité descendante](../../../2014/getting-started/backward-compatibility.md)  
  
  
