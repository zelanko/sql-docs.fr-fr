---
title: MSSQLSERVER_1807 | Microsoft Docs
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
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5799f5911e1a1b1ff87265a84a0f7950b97911a8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1807|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|CANNOT_EX_LOCK|  
|Texte du message|Impossible d'obtenir un verrou exclusif sur la base de données '%.*ls'. Recommencez l'opération ultérieurement.|  
  
## <a name="explanation"></a>Explication  
Une opération qui requérait un accès exclusif à la base de données n'a pas pu l'obtenir.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Arrêtez toutes les connexions à cette base de données ou relancez la requête ultérieurement.  
  
