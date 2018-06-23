---
title: osql ne prend plus en charge les Commandes | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8126004162280f9acbdd81266bf7dd7a2cb8f9bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051213"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a>osql ne prend plus en charge les commandes
  Le **osql** utilitaire ne prend pas en charge la **ED** et **!!** commandes.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimer les références à la **ED** et **!!** commandes à partir de vos scripts.  
  
 Si vous souhaitez utiliser le **ED** et **!!** commandes, utilisez la **sqlcmd** utilitaire au lieu de **osql**.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
