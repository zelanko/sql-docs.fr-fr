---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 865b682ec0f2a55d76ac9163da575aa5cbdaf9a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045587"
---
# <a name="localdberrortoomanysharedinstances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
    
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
  
  