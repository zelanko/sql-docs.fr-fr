---
description: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 826403e2edaee6c891a55f31ccad88469a8411cb
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506133"
---
# <a name="localdb_error_too_many_shared_instances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Détails  
  
| Attribut | Valeur |
| --------- | ----- |
|Nom du produit|SQL Server|  
|ID de l’événement|287|  
|Source de l’événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|Il existe un trop grand nombre d'instances partagées et il est impossible de générer un nom d'instance d'utilisateur unique. Annulez le partage de quelques instances partagées existantes.|  
  
## <a name="explanation"></a>Explication  
 Il existe un trop grand nombre d'instances partagées et il est impossible de générer un nom d'instance d'utilisateur unique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Annulez le partage d'une ou plusieurs instances d'exécution de base de données locale partagées et réessayez.  
  
  
