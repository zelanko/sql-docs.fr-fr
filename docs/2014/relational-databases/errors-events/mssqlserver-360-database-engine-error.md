---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21534d6cd1499634b5d93c7140b4f8f47b3e242b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551544"
---
# <a name="mssqlserver_360"></a>MSSQLSERVER_360
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|360|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DML_UPDATE_SPARSE_AND_COLSET|  
|Texte du message|La liste de colonnes cibles d'une instruction INSERT, UPDATE ou MERGE ne peut pas contenir à la fois une colonne éparse et le jeu de colonnes qui contient cette colonne éparse. Réécrivez l'instruction de manière à inclure la colonne éparse ou le jeu de colonnes, mais pas les deux.|  
  
## <a name="explanation"></a>Explication  
 Un jeu de colonnes est une représentation XML non typée qui associe certaines colonnes d’une table dans une sortie structurée. Une tentative a été effectuée de modifier à la fois le jeu de colonnes et une colonne incluse dans le jeu de colonnes, provoquant ainsi deux références à la même colonne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Réécrivez l'instruction de manière à inclure des références à la colonne ou au jeu de colonnes, mais pas aux deux.  
  
  
