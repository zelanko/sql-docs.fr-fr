---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 2c7e9da124ed3ec2fb1a0725f2f2c3050cd3484f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver9692"></a>MSSQLSERVER_9692
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9692|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB2_CANT_LISTEN_PORT_IN_USE|  
|Texte du message|Le transport de protocole %S_MSG ne peut pas écouter le port %d, car il est utilisé par un autre processus.|  
  
## <a name="explanation"></a>Explication  
Un autre programme exécuté sur l'ordinateur utilise actuellement le port TCP indiqué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez **netstat -aon** pour identifier le programme qui utilise le port. Désactivez cette application ou spécifiez un port différent pour Service Broker.  
  
