---
title: osql ne prend plus en charge les Commandes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a94c7dd28353a94da0b595183a75d239fa4c1aa2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112649"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a>osql ne prend plus en charge les commandes
  Le **osql** utilitaire ne prend pas en charge la **ED** et **!!** commandes.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimer les références à la **ED** et **!!** commandes à partir de vos scripts.  
  
 Si vous souhaitez utiliser le **ED** et **!!** commandes, utilisez le **sqlcmd** utilitaire au lieu de **osql**.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
