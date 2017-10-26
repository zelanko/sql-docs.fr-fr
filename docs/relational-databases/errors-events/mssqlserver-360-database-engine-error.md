---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4523266142da60eb89136be6209a5944cecbd5a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|360|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DML_UPDATE_SPARSE_AND_COLSET|  
|Texte du message|La liste de colonnes cibles d'une instruction INSERT, UPDATE ou MERGE ne peut pas contenir à la fois une colonne éparse et le jeu de colonnes qui contient cette colonne éparse. Réécrivez l'instruction de manière à inclure la colonne éparse ou le jeu de colonnes, mais pas les deux.|  
  
## <a name="explanation"></a>Explication  
Un jeu de colonnes est une représentation XML non typée qui associe certaines colonnes d’une table dans une sortie structurée. Une tentative a été effectuée de modifier à la fois le jeu de colonnes et une colonne incluse dans le jeu de colonnes, provoquant ainsi deux références à la même colonne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Réécrivez l'instruction de manière à inclure des références à la colonne ou au jeu de colonnes, mais pas aux deux.  
  

