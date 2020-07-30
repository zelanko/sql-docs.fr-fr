---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
ms.openlocfilehash: b07c4eebc34872868da61d7af633d29f1758e313
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246066"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a>LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Détails  
  
| Attribut | Valeur |
| --------- | ----- |
|Nom du produit|SQL Server|  
|ID de l’événement|258|  
|Source de l’événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|Impossible de créer l'instance de base de données locale avec la version spécifiée. Une instance du même nom existe déjà, mais sa version est inférieure à la version spécifiée.|  
  
## <a name="explanation"></a>Explication  
 L'instance spécifiée existe déjà mais sa version est inférieure à celle demandée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez l'instance existante et retentez l'opération.  
  
  
