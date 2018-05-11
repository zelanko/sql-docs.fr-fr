---
title: MSSQLSERVER_9004 | Microsoft Docs
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
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cbb9301d7153ba770d2c268497d5cde7a044757f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9004|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_CORRUPT|  
|Texte du message|Une erreur s'est produite lors du traitement du journal de la base de données '%.*ls'.  If possible, restore from backup. Si aucune sauvegarde n'est disponible, vous devrez peut-être recréer le journal.|  
  
## <a name="explanation"></a>Explication  
Une erreur s'est produite lors du traitement du journal, au cours d'une annulation, d'une récupération ou d'une réplication. Cela peut indiquer une erreur détectée par le système d'exploitation ou une erreur de cohérence interne détectée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Action de l'utilisateur  
L'une des actions ci-dessous corrigera cette erreur :  
  
-   Effectuez la restauration à partir d'une sauvegarde.  
  
-   Régénérez le journal.  
  
Vérifiez également les journaux des événements et les journaux des erreurs du système qui peuvent être à l'origine du problème.  
  
