---
title: MSSQLSERVER_2538 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36ba25f8653e3fd3f1287d8de5108af880f9ba7c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914487"
---
# <a name="mssqlserver2538"></a>MSSQLSERVER_2538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2538|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_ALLOCATION_SUMMARY_PER_FILE|  
|Texte du message|Fichier FILE. Nombre d'extensions = EXTENTS, pages utilisées = USED_PAGES, pages réservées = RESERVED_PAGES.|  
  
## <a name="explanation"></a>Explication  
Ces informations font partie de la sortie de la commande DBCC CHECKALLOC. Elles présentent le résumé fichier par fichier des extensions allouées, des pages utilisées et des pages réservées pour la base de données spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
