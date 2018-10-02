---
title: MSSQLSERVER_10539 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e44899e6b586610dc9b18e3ab2e4ec31d4451c1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625527"
---
# <a name="mssqlserver10539"></a>MSSQLSERVER_10539
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10539|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NO_PLAN_FOR_STMT|  
|Texte du message|Impossible de créer le repère de plan '%.*ls' à partir du cache, car aucun plan de requête n'est disponible pour l'instruction avec l'offset de démarrage %d. Ce problème peut se produire si l'instruction dépend des objets de base de données qui n'ont pas encore été créés. Assurez-vous que tous les objets de base de données nécessaires existent, puis exécutez l'instruction avant de créer le repère de plan.|  
  
## <a name="explanation"></a>Explication  
Aucun plan de requête n'est disponible dans le cache du plan pour l'instruction avec l'offset de démarrage spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Assurez-vous que tous les objets de base de données nécessaires existent, puis exécutez l'instruction avant de créer le repère de plan.  
  
## <a name="see-also"></a> Voir aussi  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
