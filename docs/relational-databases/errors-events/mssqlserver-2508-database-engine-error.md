---
description: MSSQLSERVER_2508
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9d45680a532698883e5fe8076af79f851ce47ab8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482837"
---
# <a name="mssqlserver_2508"></a>MSSQLSERVER_2508
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|2508|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|Texte du message|Le nombre %.*ls pour l’objet « %.\*ls », ID d’index %d, ID de partition %I64d, ID d’unité d’allocation %I64d (type %.\*ls) est incorrect. Exécutez DBCC UPDATEUSAGE.|  
  
## <a name="explanation"></a>Explication  
Dans les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les valeurs du nombre de lignes de table et d'index et du nombre de pages peuvent être incorrectes. Les bases de données créées avec des versions antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] peuvent contenir des nombres incorrects. DBCC CHECKDB a été amélioré pour détecter ces erreurs et retourne ce message d'avertissement lorsque l'erreur se produit.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez DBCC UPDATEUSAGE sur l'objet ou l'index spécifié ou sur la base de données qui contient l'objet pour corriger les nombres non valides.  
  
