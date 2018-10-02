---
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
manager: craigg
ms.openlocfilehash: eab10bb8a76a0c82ee03c19c12f907d0a117a648
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606768"
---
# <a name="mssqlserver2508"></a>MSSQLSERVER_2508
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2508|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|Texte du message|Le nombre %.*ls pour l’objet « %.\*ls », ID d’index %d, ID de partition %I64d, ID d’unité d’allocation %I64d (type %.\*ls) est incorrect. Exécutez DBCC UPDATEUSAGE.|  
  
## <a name="explanation"></a>Explication  
Dans les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les valeurs du nombre de lignes de table et d'index et du nombre de pages peuvent être incorrectes. Les bases de données créées avec des versions antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] peuvent contenir des nombres incorrects. DBCC CHECKDB a été amélioré pour détecter ces erreurs et retourne ce message d'avertissement lorsque l'erreur se produit.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez DBCC UPDATEUSAGE sur l'objet ou l'index spécifié ou sur la base de données qui contient l'objet pour corriger les nombres non valides.  
  
