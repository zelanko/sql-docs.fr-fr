---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e811d36160cf0a4477452acec336c61bf52e793
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62868066"
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
  
  
