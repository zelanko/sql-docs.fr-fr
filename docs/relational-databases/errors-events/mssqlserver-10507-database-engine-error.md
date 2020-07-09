---
title: MSSQLSERVER_10507 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 82d21d961f623ee20625f0fefd9fc4403f000e96
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781506"
---
# <a name="mssqlserver_10507"></a>MSSQLSERVER_10507
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|10507|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_STMT_DOES_NOT_MATCH|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car l’instruction spécifiée par **\@stmt** et **\@module_or_batch** ou par **\@plan_handle** et **\@statement_start_offset** ne correspond à aucune instruction dans le module ou lot spécifié. Modifiez les valeurs pour qu'elles correspondent à une instruction dans le module ou le lot.|  
  
## <a name="explanation"></a>Explication  
Une instruction dans le module ou le lot spécifié n'a pas pu être mise en correspondance avec l'instruction ou la valeur de décalage de l'instruction spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Modifiez les valeurs de paramètre spécifiées pour qu'elles correspondent à une instruction dans le module ou le lot.  
  
## <a name="see-also"></a>Voir aussi  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
