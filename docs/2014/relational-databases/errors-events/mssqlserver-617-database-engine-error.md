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
ms.openlocfilehash: dedf0b9ae26e7c2c1bb2c3251a1df10a3577f96d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053774"
---
# <a name="mssqlserver_617"></a>MSSQLSERVER_617
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|617|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NODESHASH|  
|Texte du message|Le descripteur de l'ID d'objet %ld dans l'ID de base de données %d n'a pas été trouvé dans la table de hachage lors de la tentative de déhachage. Une entrée est manquante dans une table de travail. Réexécutez la requête. Si un curseur est concerné, fermez et rouvrez le curseur.|  
  
## <a name="explanation"></a>Explication  
 SQL Server ne peut pas localiser la table de travail pour une entrée spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Si un curseur est impliqué, fermez et rouvrez celui-ci.  
  
2.  Réexécutez la requête.  
  
  
