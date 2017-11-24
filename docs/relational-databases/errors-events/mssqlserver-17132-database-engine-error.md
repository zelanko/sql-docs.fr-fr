---
title: MSSQLSERVER_17132 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3ea493efb21a7d2f0ed50ef92cb314de394be74
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
  
