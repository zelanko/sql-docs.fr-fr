---
title: MSSQLSERVER_2519 | Microsoft Docs
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
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4fdcb3ccc1ccbc22f179a851b5d77ae45ab925e6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2519|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_NO_EXPRESSION_EVALUATOR|  
|Texte du message|Impossible de vérifier les colonnes calculées et les types définis par l'utilisateur pour l'ID d'objet O_ID (objet « O_NAME ») car l'évaluateur d'expression interne n'a pas pu être initialisé.|  
  
## <a name="explanation"></a>Explication  
Ce message d'information indique que le processeur de requêtes n'a pas pu fournir à DBCC un objet interne pour permettre l'évaluation de colonnes calculées et de types clr (common language runtime) définis par l'utilisateur. Cela signifie que l'exactitude des colonnes calculées et des types clr définis par l'utilisateur ne sera pas vérifiée et que ceux-ci ne seront pas utilisés lorsque DBCC vérifiera la cohérence entre les index et les tables de base.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
## <a name="see-also"></a> Voir aussi  
[MSSQLSERVER_2518](~/relational-databases/errors-events/mssqlserver-2518-database-engine-error.md)  
  
