---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ad7526bc49d8113c6ae6a276a75786aecc001ae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633464"
---
# <a name="mssqlserver41359"></a>MSSQLSERVER_41359
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
Définissez READ_COMMITTED_SNAPSHOT sur OFF, ou fournissez un niveau d’isolement pris en charge pour la table optimisée en mémoire à l’aide d’un indicateur au niveau de la table, comme WITH (SNAPSHOT). Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
