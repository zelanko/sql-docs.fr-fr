---
title: osql ne prend plus en charge les commandes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ce7bfa0bbeec5c5ca83b7139f0ff28e3994021d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093717"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a>osql ne prend plus en charge les commandes
  L’utilitaire **osql** ne prend pas en charge les **Ed** et **!!** commandes.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez les références aux **Ed** et **!!** commandes de vos scripts.  
  
 Si vous souhaitez utiliser le **Ed** et **!!** des commandes, utilisez l’utilitaire **sqlcmd** au lieu de **osql**.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
