---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb7b1eb95cd1b412368be74052af2a1cd2d9d145
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="localdberrortoomanysharedinstances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|287|  
|Source de l'événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|Il existe un trop grand nombre d'instances partagées et il est impossible de générer un nom d'instance d'utilisateur unique. Annulez le partage de quelques instances partagées existantes.|  
  
## <a name="explanation"></a>Explication  
 Il existe un trop grand nombre d'instances partagées et il est impossible de générer un nom d'instance d'utilisateur unique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Annulez le partage d'une ou plusieurs instances d'exécution de base de données locale partagées et réessayez.  
  
  
