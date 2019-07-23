---
title: MSSQLSERVER_17084 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6e18eff965ac406ffd764bbe01bd9bb1aff41437
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076713"
---
# <a name="mssqlserver17084"></a>MSSQLSERVER_17084
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|17084|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|P3_ATOMIC_WITH_MISSING_OPTION|  
|Texte du message|La clause WITH de l'instruction BEGIN ATOMIC doit spécifier une valeur pour l'option « %ls ».|  
  
## <a name="explanation"></a>Explication  
La clause WITH de l'instruction BEGIN ATOMIC n'a pas spécifié de valeur pour une option.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Les blocs **ATOMIC** requièrent des valeurs pour les options **WITH** **TRANSACTION ISOLATION LEVEL** et **LANGUAGE**. Par exemple :  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
