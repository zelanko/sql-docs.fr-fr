---
title: Serveurs de publications non-SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f15f07dbf294d697afd385318f3dbf1447c8e2d8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068609"
---
# <a name="non-sql-server-publishers"></a>serveurs de publications non-SQL Server
  La publication de données à partir de sources non- [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vous permet de consolider les données dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut s'abonner à des données transactionnelles ou à des données d'instantané à partir d'une base de données Oracle. Pour plus d’informations sur la publication à partir d’Oracle, consultez [Présentation de la publication Oracle](oracle-publishing-overview.md).  
  
 La réplication hétérogène sur les abonnés non SQL Server est déconseillée. La publication Oracle est déconseillée. Pour déplacer des données, créez des solutions à l'aide de la Capture de données modifiées et [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 La publication à partir de bases de données non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est idéale pour les scénarios suivants :  
  
|Scénario|Description|  
|--------------|-----------------|  
|Déploiements d'applications[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Développez avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en exploitant des données répliquées à partir d’une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Serveurs de secours pour l'entreposage des données|Gardez les bases de données intermédiaires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] synchronisées avec une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Migration vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Testez votre application en temps réel sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tout en répliquant les changements du système source. Basculez vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque vous êtes satisfait de la migration.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](heterogeneous-database-replication.md)  
  
  
