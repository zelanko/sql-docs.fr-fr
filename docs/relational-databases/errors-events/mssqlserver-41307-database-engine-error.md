---
description: MSSQLSERVER_41307
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
ms.openlocfilehash: 6a19c447c70769c6be45b5a69f025f63c08fc17e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428721"
---
# <a name="mssqlserver_41307"></a>MSSQLSERVER_41307
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
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
  
