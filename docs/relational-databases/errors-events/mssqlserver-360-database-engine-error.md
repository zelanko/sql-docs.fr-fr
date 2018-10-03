---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e250985c9f1dc2ed043c55d9182b932e00dc1365
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832807"
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
