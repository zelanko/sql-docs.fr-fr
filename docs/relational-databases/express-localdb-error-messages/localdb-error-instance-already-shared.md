---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 636080d7247345cca8f6a6b74fbd19c9e8a487d9
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246141"
---
# <a name="localdb_error_instance_already_shared"></a>LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Détails  
  
| Attribut | Valeur |
| --------- | ----- |
|Nom du produit|SQL Server|  
|ID de l’événement|284|  
|Source de l’événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|L'instance de base de données locale spécifiée est déjà partagée.|  
  
## <a name="explanation"></a>Explication  
 L'instance de base de données locale spécifiée est déjà partagée avec un nom différent.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Annulez le partage de l'instance partagée avant de la partager de nouveau avec un nom différent.  
  
  
