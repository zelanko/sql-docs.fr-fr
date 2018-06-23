---
title: MSSQLSERVER_41359 | Microsoft Docs
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
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6fc668ebab849134cc7e6fb4099c03588f1ad1e8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144529"
---
# <a name="mssqlserver41359"></a>MSSQLSERVER_41359
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41359|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Texte du message|Une requête qui accède à des tables optimisées en mémoire selon le niveau d'isolement READ COMMITTED ne peut pas accéder aux tables sur disque lorsque l'option READ_COMMITTED_SNAPSHOT de la base de données a la valeur ON. Spécifiez un niveau d'isolement pris en charge pour la table optimisée en mémoire à l'aide d'un indicateur de table, comme WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Explication  
 La base de données avec READ_COMMITTED_SNAPSHOT=ON ne prend pas en charge les transactions qui accèdent aux tables optimisées en mémoire et aux tables sur disque.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Définissez READ_COMMITTED_SNAPSHOT sur OFF, ou fournissez un niveau d’isolement pris en charge pour la table optimisée en mémoire à l’aide d’un indicateur au niveau de la table, comme WITH (SNAPSHOT). Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  