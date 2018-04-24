---
title: MSSQLSERVER_12304 | Microsoft Docs
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
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
caps.latest.revision: 4
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93b4beb33bb58f9e0e5c87fcd7b02f515fbd6fff
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver12304"></a>MSSQLSERVER_12304
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|12304|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_UNSUPPORTED_IDENTITY_TABLE_VAR|  
|Texte du message|L'utilisation d'un type de table optimisée en mémoire utilisant la propriété IDENTITY avec l'une de ses colonnes n'est pas prise en charge lors de l'utilisation du type hors du contexte de la procédure stockée compilée en mode natif.|  
  
## <a name="user-action"></a>Action de l'utilisateur  
N'utilisez pas un type de table optimisée en mémoire qui utilise la propriété d'identité avec l'une de ses colonnes.  
  
## <a name="see-also"></a> Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
