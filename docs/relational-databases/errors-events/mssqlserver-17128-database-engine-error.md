---
title: MSSQLSERVER_17128 | Microsoft Docs
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
helpviewer_keywords: 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10284d4192b05ff7fac278e5a02e33384982517f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17128|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NOBUFSPACE|  
|Texte du message|initdata : aucune mémoire pour les tampons du noyau.|  
  
## <a name="explanation"></a>Explication  
Les réservations ou les allocations de mémoire initiales du pool de mémoires tampons ont échoué, et SQL Server se termine.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Provoqué généralement par le démarrage de SQL Server sur un ordinateur extrêmement petit, beaucoup plus petit que la configuration requise minimale.  
  
