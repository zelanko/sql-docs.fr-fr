---
title: MSSQLSERVER_10533 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7748f025a36bbfd29b11e0f7c982fa36f317c6e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47703537"
---
# <a name="mssqlserver10533"></a>MSSQLSERVER_10533
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10533|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NAME_TOO_BIG|  
|Texte du message|Impossible de créer le repère de plan '%.*ls', car le nom du repère de plan dépasse 124, le nombre maximal de caractères autorisé. Indiquez un nom qui contient moins de 125 caractères.|  
  
## <a name="explanation"></a>Explication  
Le nom du repère de plan dépasse 124 caractères, le nombre maximal autorisé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Indiquez un nom qui contient moins de 125 caractères.  
  
## <a name="see-also"></a> Voir aussi  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
