---
title: MSSQLSERVER_41307 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7080c7814fdbff436bbc7e27bb5cba4c2da227e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68043460"
---
# <a name="mssqlserver_41307"></a>MSSQLSERVER_41307
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41307|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_HEKATON_ROW_LIMIT|  
|Texte du message|La limite de taille de ligne de *nombre* octets pour les tables optimisées en mémoire a été atteinte. Veuillez simplifier la définition de la table.|  
  
## <a name="explanation"></a>Explication  
La limite de taille ligne pour les tables optimisées en mémoire est de 8 060 octets. Pour plus d’informations, consultez [Taille de la table et des lignes dans les tables optimisées en mémoire](~/relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md). Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
