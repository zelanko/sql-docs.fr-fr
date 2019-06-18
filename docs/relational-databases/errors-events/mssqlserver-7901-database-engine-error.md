---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d3eeee976a45817b155c86ae99bd2cbd229324d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62694454"
---
# <a name="mssqlserver7901"></a>MSSQLSERVER_7901
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7901|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Texte du message|L’instruction de réparation n’a pas été traitée. Ce niveau de réparation n'est pas pris en charge lorsque la base de données est en mode d'urgence.|  
  
## <a name="explanation"></a>Explication  
La base de données est en mode d'urgence et un niveau de réparation autre que REPAIR_ALLOW_DATA_LOSS a été spécifié. Les réparations ne peuvent pas être effectuées en mode d'urgence si REPAIR_ALLOW_DATA_LOSS n'est pas spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez de nouveau la commande et spécifiez l'option REPAIR_ALLOW_DATA_LOSS.  
  
