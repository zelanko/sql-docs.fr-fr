---
title: MSSQLSERVER_10521 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f86922211e670cb59b4541071e9e7d7f67302bc9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068154"
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10521|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_PARAM_NEEDED|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car **@type** a été spécifié en tant que '%ls' et le paramètre '%ls' a la valeur Null. Ce type requiert une valeur autre que Null pour le paramètre. Spécifiez une valeur autre que Null pour le paramètre ou remplacez le type par un type qui autorise une valeur Null pour le paramètre.|  
  
## <a name="explanation"></a>Explication  
Le type spécifié dans **@type** nécessite une valeur non Null pour le paramètre spécifié, mais une valeur Null a été fournie.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Spécifiez une valeur autre que Null pour le paramètre ou remplacez le type par un type qui autorise une valeur Null pour le paramètre.  
  
## <a name="see-also"></a>Voir aussi  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
