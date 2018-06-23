---
title: MSSQLSERVER_7920 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: bcb388953f3795fb8f654107a414ca4c7587df8d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151916"
---
# <a name="mssqlserver7920"></a>MSSQLSERVER_7920
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7920|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_SUMMARY_ENTRIES|  
|Texte du message|ENTRY_COUNT entrées traitées dans le catalogue système pour la base de données ID D_ID.|  
  
## <a name="explanation"></a>Explication  
 Ce message est retourné à titre d'information par toutes les commandes DBCC CHECK à l'exception de DBCC CHECKALLOC. La valeur retournée est le nombre total d'ensembles de lignes vérifiés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 None  
  
  