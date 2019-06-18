---
title: MSSQLSERVER_7920 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97855e4cc5b0bd9e28ef2de69622291ff175cc88
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62797116"
---
# <a name="mssqlserver7920"></a>MSSQLSERVER_7920
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
