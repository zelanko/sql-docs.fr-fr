---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1748e8b483eecee43da921bd268d419408924af3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062018"
---
# <a name="mssqlserver2511"></a>MSSQLSERVER_2511
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2511|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_KEYS_OUT_OF_ORDER|  
|Texte du message|Erreur de table : ID d'objet %d, ID d'index %d, ID de partition %I64d, ID d'unité d'allocation %I64d (type %.*ls). Les clés sont désordonnées sur la page %S_PGID, slots %d et %d.|  
  
## <a name="explanation"></a>Explication  
 Des clés désordonnées ont été détectées dans l'index spécifié. La page qui contient ces clés peut être endommagée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Reconstruisez l'index spécifié en utilisant l'instruction ALTER INDEX REBUILD.  
  
  
