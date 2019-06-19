---
title: MSSQLSERVER_10737 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f96a3849360cc0eb5d04c75187f505967b33baf3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048263"
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
