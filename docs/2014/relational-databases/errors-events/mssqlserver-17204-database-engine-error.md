---
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2fd28a126b3a0a7f833c6410d4e590b5dc07e5a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869614"
---
# <a name="mssqlserver17204"></a>MSSQLSERVER_17204
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17204|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBLKIO_DEVOPENFAILED|  
|Texte du message|%ls : impossible d’ouvrir le fichier %ls pour le numéro de fichier %d.  Erreur de système d'exploitation : %ls.|  
  
## <a name="explanation"></a>Explication  
SQL Server n'a pas pu ouvrir le fichier spécifié en raison de l'erreur spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Diagnostiquez et corrigez le système d'exploitation, puis réessayez l'opération.  
  
