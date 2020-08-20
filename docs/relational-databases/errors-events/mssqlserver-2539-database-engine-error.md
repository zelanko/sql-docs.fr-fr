---
description: MSSQLSERVER_2539
title: MSSQLSERVER_2539 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a3c22d94c510dcff4f1eb6d9c8a4b0af8b98486
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456261"
---
# <a name="mssqlserver_2539"></a>MSSQLSERVER_2539
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|2539|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_ALLOCATION_SUMMARY_FOR_DATABASE|  
|Texte du message|Nombre total d'extensions = EXTENTS, pages utilisées = USED_PAGES et pages réservées = RESERVED_PAGES dans cette base de données.|  
  
## <a name="explanation"></a>Explication  
Ces informations font partie de la sortie de la commande DBCC CHECKALLOC. Ces informations correspondent au résumé des extensions allouées, des pages utilisées et des pages réservées pour la base de données spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
