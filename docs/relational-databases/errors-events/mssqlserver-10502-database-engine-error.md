---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b6120a7f5c0479bb23894d1368c903a27f1de65
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781521"
---
# <a name="mssqlserver_10502"></a>MSSQLSERVER_10502
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|10502|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_DUP_FOUND|  
|Texte du message|Impossible de créer le repère de plan '%.*ls', car l’instruction spécifiée par @stmt et @module_or_batch ou par @plan_handle et @statement_start_offset correspond au repère de plan existant '%.\*ls' dans la base de données. Supprimez le repère de plan existant avant de créer le nouveau.|  
  
## <a name="explanation"></a>Explication  
Un repère de plan existe pour l'instruction spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Supprimez le repère de plan existant avant de créer le nouveau.  
  
## <a name="see-also"></a>Voir aussi  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
