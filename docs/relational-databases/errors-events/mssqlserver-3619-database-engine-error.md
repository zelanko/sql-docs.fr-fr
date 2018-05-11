---
title: MSSQLSERVER_3619 | Microsoft Docs
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
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2919c31191d87f032e89512317548c5b3be0f47b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3619|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SYS_NOLOG|  
|Texte du message|Impossible d'écrire un enregistrement de point de contrôle dans la base de données ID %d car le journal est saturé. Demandez à l'administrateur de la base de données de tronquer ce journal ou d'allouer davantage d'espace aux fichiers journaux de la base de données.|  
  
## <a name="explanation"></a>Explication  
Le journal des transactions est saturé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Tronquez le journal pour libérer de l'espace ou allouez plus d'espace au journal. Pour plus d'informations, consultez « Résolution des problèmes en cas de journal des transactions saturé (erreur 9002) » dans la documentation en ligne de SQL Server.  
  
