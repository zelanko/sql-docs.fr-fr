---
title: MSSQLSERVER_10737 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: a5fef9ff1b72130ae5cb935a27e5ad82fc616d66
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|MSSQLSERVER|  
|ID d'événement|10737|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|REBUILD_PARTITION_ALL_NOT_SPECIFIED|  
|Texte du message|Dans une instruction ALTER TABLE REBUILD ou ALTER INDEX REBUILD, lorsqu'une partition est spécifiée dans une clause DATA_COMPRESSION, PARTITION=ALL est obligatoire. La clause PARTITION=ALL permet d'imposer que toutes les partitions de la table ou de l'index soient régénérées, même si un seul sous-ensemble est spécifié dans la clause DATA_COMPRESSION.|  
  
## <a name="user-action"></a>Action de l'utilisateur  
Ajoutez la clause PARTITION=ALL à l'instruction ALTER TABLE ou ALTER INDEX. Ou, pour reconstruire une partition spécifique, utilisez REBUILD PARTITION = \<expression_numéro_partition> WITH (DATA_COMPRESSION={ON | OFF}).  
  
