---
title: MSSQLSERVER_17132 | Microsoft Docs
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
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 64d3004e0e393d4c3f78a171a8d2a8bc9b37eb6e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17132"></a>MSSQLSERVER_17132
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17132|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NODESSPACE|  
|Texte du message|Échec du démarrage du serveur en raison d'une quantité de mémoire insuffisante pour le descripteur. Réduisez les utilisations non vitales de la mémoire ou augmentez la mémoire système.|  
  
## <a name="explanation"></a>Explication  
Échec de l'allocation d'une quantité de mémoire suffisante pour stocker le descripteur interne du serveur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Ajoutez plus de mémoire à l'ordinateur. Les étapes de résolution des problèmes de mémoire génériques peuvent être utiles.  
  
