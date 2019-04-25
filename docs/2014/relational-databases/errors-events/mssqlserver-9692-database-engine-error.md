---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 661d7ab65afca258424af300debde328b8f01fee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761709"
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
 Exécutez `netstat -aon` pour déterminer le programme qui utilise le port. Désactivez cette application ou spécifiez un port différent pour Service Broker.  
  
  
