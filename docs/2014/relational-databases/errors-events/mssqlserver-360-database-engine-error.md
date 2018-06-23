---
title: MSSQLSERVER_360 | Microsoft Docs
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2300cb7f2e45ca9ab76b9c8b7da23e5cb59e364c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040891"
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
  
  