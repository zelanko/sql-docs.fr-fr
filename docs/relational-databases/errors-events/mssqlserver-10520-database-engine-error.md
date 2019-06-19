---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3489ebb4fcd8b741aa3b77234ef2d7f81f3b64f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048593"
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10520|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_PARAM_NOT_ALLOWED|  
|Texte du message|Impossible de créer le repère de plan ’%.ls’, car @type a été spécifié comme ’%ls’ et une valeur autre que Null est spécifiée pour le paramètre ’%ls’. Ce type requiert une valeur Null pour le paramètre. Spécifiez la valeur Null pour le paramètre ou remplacez le type par un type qui autorise une valeur autre que Null pour le paramètre.|  
  
## <a name="explanation"></a>Explication  
Le type spécifié dans @type nécessite une valeur Null pour le paramètre spécifié, mais une valeur non Null a été fournie.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Spécifiez la valeur Null pour le paramètre ou remplacez le type par un type qui autorise une valeur autre que Null pour le paramètre.  
  
## <a name="see-also"></a>Voir aussi  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
  
