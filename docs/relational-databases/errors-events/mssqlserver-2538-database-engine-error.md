---
description: MSSQLSERVER_2538
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
ms.openlocfilehash: c4d083a389ffb80760f025cfeaa95f5f3bbac6ab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456271"
---
# <a name="mssqlserver_2538"></a>MSSQLSERVER_2538
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|2538|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_ALLOCATION_SUMMARY_PER_FILE|  
|Texte du message|Fichier FILE. Nombre d'extensions = EXTENTS, pages utilisées = USED_PAGES, pages réservées = RESERVED_PAGES.|  
  
## <a name="explanation"></a>Explication  
Ces informations font partie de la sortie de la commande DBCC CHECKALLOC. Elles présentent le résumé fichier par fichier des extensions allouées, des pages utilisées et des pages réservées pour la base de données spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
