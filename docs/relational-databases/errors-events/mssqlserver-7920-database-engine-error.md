---
title: MSSQLSERVER_7920 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60c6977e5698ffd71576f64de9496a4989afa1b1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver7920"></a>MSSQLSERVER_7920
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7920|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_SUMMARY_ENTRIES|  
|Texte du message|ENTRY_COUNT entrées traitées dans le catalogue système pour la base de données ID D_ID.|  
  
## <a name="explanation"></a>Explication  
Ce message est retourné à titre d'information par toutes les commandes DBCC CHECK à l'exception de DBCC CHECKALLOC. La valeur retournée est le nombre total d'ensembles de lignes vérifiés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
