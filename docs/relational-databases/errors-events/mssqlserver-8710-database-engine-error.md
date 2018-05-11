---
title: MSSQLSERVER_8710 | Microsoft Docs
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
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 28b8eb71cc0e50925788596d1b23572a51064423
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|MSSQLSERVER|  
|ID d'événement|8710|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|Texte du message|Les fonctions d'agrégation utilisées avec les requêtes CUBE, ROLLUP ou GROUPING SET doivent permettre la fusion des sous-agrégats. Pour résoudre ce problème, supprimez la fonction d'agrégation ou écrivez la requête en utilisant UNION ALL sur les clauses GROUP BY.|  
  
## <a name="explanation"></a>Explication  
Une fonction d'agrégation a été utilisée avec des requêtes CUBE, ROLLUP ou GROUPING SET qui ne fournit pas de méthode pour fusionner les sous-agrégats.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour résoudre ce problème, supprimez la fonction d'agrégation ou écrivez la requête en utilisant UNION ALL sur les clauses GROUP BY.  
  
