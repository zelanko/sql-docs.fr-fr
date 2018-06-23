---
title: MSSQLSERVER_8689 | Microsoft Docs
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
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c6716439038f61003abd807cefbf123ec3682b17
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142734"
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8689|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|USEPLAN_ERR_NO_DB|  
|Texte du message|La base de données '%.*ls' spécifiée dans l'indicateur USE PLAN n'existe pas. Indiquez une base de données existante.|  
  
## <a name="explanation"></a>Explication  
 Une base de données spécifiée dans l'indicateur USE PLAN n'existe pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Veillez à ce que toutes les bases de données spécifiées dans l'indicateur USE PLAN existent.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de requête &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)   
 [Repères de plan](../performance/plan-guides.md)  
  
  
