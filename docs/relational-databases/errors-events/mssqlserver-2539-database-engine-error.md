---
title: MSSQLSERVER_2539 | Microsoft Docs
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
- 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26c4dd19ac5e09e39e431d650390eb012ec192e8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2539"></a>MSSQLSERVER_2539
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2539|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_ALLOCATION_SUMMARY_FOR_DATABASE|  
|Texte du message|Nombre total d'extensions = EXTENTS, pages utilisées = USED_PAGES et pages réservées = RESERVED_PAGES dans cette base de données.|  
  
## <a name="explanation"></a>Explication  
Ces informations font partie de la sortie de la commande DBCC CHECKALLOC. Ces informations correspondent au résumé des extensions allouées, des pages utilisées et des pages réservées pour la base de données spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
