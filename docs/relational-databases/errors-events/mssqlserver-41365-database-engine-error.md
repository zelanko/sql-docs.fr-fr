---
title: MSSQLSERVER_41365 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 841ea749faa87d66216754ce3aabb61c03d6f996
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765309"
---
# <a name="mssqlserver_41365"></a>MSSQLSERVER_41365
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41365|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_MERGE_SCHEDULE_ERROR|  
|Texte du message|La demande de fusion de la plage des transactions [%d, %d] dans la base de données %.*ls n'a pas été planifiée. Les fichiers de point de contrôle représentant la plage sont soit indisponibles pour la fusion, soit ils font partie d'une fusion en cours.|  
  
## <a name="explanation"></a>Explication  
Les fichiers de point de contrôle représentant la plage sont soit indisponibles pour la fusion, soit ils font partie d'une fusion en cours.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Optimisez la plage de transactions pour les opérations de fusion/attente avant de réexécuter la même demande. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
