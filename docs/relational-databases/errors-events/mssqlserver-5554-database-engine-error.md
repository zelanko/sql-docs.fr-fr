---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 496718ec066f690ddd6e14e9937e356b40ef819b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|MSSQLSERVER|  
|ID d'événement|5554|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|FS_MINIVER_OVERFLOW|  
|Texte du message|La limite maximale du nombre total de versions d'un seul fichier pour le système de fichiers a été atteinte.|  
  
## <a name="explanation"></a>Explication  
Dans les scénarios de déclencheur ou MARS (Multiple Active Result Set), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise la miniversion spécifiée par le système d’exploitation.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Essayez d'éviter les mises à jour répétées des données dans la même transaction.  
  
