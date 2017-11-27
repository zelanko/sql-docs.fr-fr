---
title: MSSQLSERVER_17803 | Microsoft Docs
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
helpviewer_keywords: 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 683a66793d0755d31469b09434090c87e931cbec
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17803|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SRV_NOMEMORY|  
|Texte du message|Une erreur d'allocation de mémoire s'est produite au cours de l'établissement de la connexion. Réduisez la charge de mémoire qui n'est pas essentielle ou augmentez la quantité de mémoire système. La connexion a été fermée.%.*ls|  
  
## <a name="explanation"></a>Explication  
Le serveur manque de mémoire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Déterminez la cause de la mémoire insuffisante au niveau du serveur. Les étapes de résolution des problèmes de mémoire génériques peuvent être utiles  
  
