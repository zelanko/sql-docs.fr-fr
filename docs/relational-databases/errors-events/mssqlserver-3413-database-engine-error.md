---
title: MSSQLSERVER_3413 | Microsoft Docs
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
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9cfa7a7f5b40767776c0db4ac58918ccf45080f4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3413|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|MARKDB|  
|Texte du message|ID base de données %d. Impossible de marquer la base de données comme suspecte. Échec de l'analyse Getnext NC sur sys.databases.database_id. Consultez les erreurs précédentes dans le journal des erreurs afin d'identifier la cause, puis corrigez tous les problèmes associés.|  
  
## <a name="explanation"></a>Explication  
Une erreur inattendue s'est produite lors d'une tentative de marquage SUSPECT d'une base de données utilisateur dans le catalogue. L'état SUSPECT ne peut pas être persistant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Consultez les erreurs précédentes et corrigez le problème.  
  
