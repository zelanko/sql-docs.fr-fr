---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f63983243d0859fcb7ebaaf1ac5d184757d1f274
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099771"
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|617|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NODESHASH|  
|Texte du message|Le descripteur de l'ID d'objet %ld dans l'ID de base de données %d n'a pas été trouvé dans la table de hachage lors de la tentative de déhachage. Une entrée est manquante dans une table de travail. Réexécutez la requête. Si un curseur est concerné, fermez et rouvrez le curseur.|  
  
## <a name="explanation"></a>Explication  
 SQL Server ne peut pas localiser la table de travail pour une entrée spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Si un curseur est impliqué, fermez et rouvrez celui-ci.  
  
2.  Réexécutez la requête.  
  
  
