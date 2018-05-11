---
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75eab047579e11812abe1aef15b13dde82dc1fb9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17204"></a>MSSQLSERVER_17204
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17204|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBLKIO_DEVOPENFAILED|  
|Texte du message|%ls : impossible d'ouvrir le fichier %ls pour le numéro de fichier %d.  Erreur de système d'exploitation : %ls.|  
  
## <a name="explanation"></a>Explication  
SQL Server n'a pas pu ouvrir le fichier spécifié en raison de l'erreur spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Diagnostiquez et corrigez le système d'exploitation, puis réessayez l'opération.  
  
