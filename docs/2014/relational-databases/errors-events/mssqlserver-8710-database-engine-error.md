---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 79c9fc7c9c15d83dafc8d117e142fc06741c11ee
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216504"
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
  
  
