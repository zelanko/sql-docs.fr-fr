---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 90e446493651140fff2fa670847e0a25d588f381
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154390"
---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|MSSQLSERVER|  
|ID d'événement|3937|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XACT_FILESTREAM_ROLLBACK_ERROR|  
|Texte du message|Une erreur s'est produite en tentant d'avertir le pilote de filtre FILESTREAM qu'une transaction était restaurée. Code d'erreur : 0x%0x.|  
  
## <a name="explanation"></a>Explication  
 Une erreur a été retournée par le pilote RsFx lors de la publication d'une notification de restauration pour une transaction. Cela est probablement dû à une insuffisance de ressources. Cela peut provoquer une petite fuite de mémoire dans le pilote de filtre RsFx, mais elle sera libérée lorsque le processus sqlservr.exe qui a créé la transaction se terminera.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  