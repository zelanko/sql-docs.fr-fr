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
ms.openlocfilehash: b740f7be7512f73bfe5c6d570ce3a97464a163fe
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553014"
---
# <a name="mssqlserver_9692"></a>MSSQLSERVER_9692
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|9692|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB2_CANT_LISTEN_PORT_IN_USE|  
|Texte du message|Le transport de protocole %S_MSG ne peut pas écouter le port %d, car il est utilisé par un autre processus.|  
  
## <a name="explanation"></a>Explication  
 Un autre programme exécuté sur l'ordinateur utilise actuellement le port TCP indiqué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez `netstat -aon` pour déterminer le programme qui utilise le port. Désactivez cette application ou spécifiez un port différent pour Service Broker.  
  
  
