---
title: MSSQLSERVER_2538 | Microsoft Docs
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
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a3630d0441bd067a1dc78e41b997d4d51d6c7fc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2538"></a>MSSQLSERVER_2538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2538|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_ALLOCATION_SUMMARY_PER_FILE|  
|Texte du message|Fichier FILE. Nombre d'extensions = EXTENTS, pages utilisées = USED_PAGES, pages réservées = RESERVED_PAGES.|  
  
## <a name="explanation"></a>Explication  
Ces informations font partie de la sortie de la commande DBCC CHECKALLOC. Elles présentent le résumé fichier par fichier des extensions allouées, des pages utilisées et des pages réservées pour la base de données spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
