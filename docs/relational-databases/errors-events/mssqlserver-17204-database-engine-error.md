---
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: befada4a3c2b5ea56fbe8c6ec6b14f6d5a558886
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
  
