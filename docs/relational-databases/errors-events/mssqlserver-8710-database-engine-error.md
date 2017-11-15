---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 427ae245dc58fddae8b9c78145a8a6601839ed7e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
  
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
  
