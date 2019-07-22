---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc5fb10b9c00d5b309c787c0a7e127e47a3be9f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138583"
---
# <a name="mssqlserver2511"></a>MSSQLSERVER_2511
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2511|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_KEYS_OUT_OF_ORDER|  
|Texte du message|Erreur de table, ID d’objet %d, ID d’index %d, ID de partition %I64d, ID d’unité d’allocation %I64d (type %.*ls). Les clés sont désordonnées sur la page %S_PGID, slots %d et %d.|  
  
## <a name="explanation"></a>Explication  
Des clés désordonnées ont été détectées dans l'index spécifié. La page qui contient ces clés peut être endommagée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Reconstruisez l'index spécifié en utilisant l'instruction ALTER INDEX REBUILD.  
  
