---
title: MSSQLSERVER_3452 | Microsoft Docs
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
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b6ef54d9a48826e67d1fbf8b3673a590a2c58962
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152582"
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3452|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|REC_CHECKIDENTITY|  
|Texte du message|La récupération de la base de données '%.*ls' (%d) a détecté une possible incohérence de valeurs d'identité dans la table ID %d. Exécutez DBCC CHECKIDENT (’%.\*ls’).|  
  
## <a name="explanation"></a>Explication  
 Au cours de la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le processus de récupération des valeurs d'identité dans la base de données a détecté une incohérence dans les métadonnées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez DBCC CHECKIDENT.  
  
  