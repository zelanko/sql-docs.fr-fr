---
title: MSSQLSERVER_17083 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 917a7b70b8ba4808d1698a6fa2d566c5f399b9d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47748357"
---
# <a name="mssqlserver17083"></a>MSSQLSERVER_17083
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|17083|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|P3_HEKATON_NOT_ATOMIC|  
|Texte du message|Le corps d'une procédure stockée compilée en mode natif doit être un bloc ATOMIC.|  
  
## <a name="explanation"></a>Explication  
Le corps d'une procédure stockée compilée en mode natif n'avait pas un bloc ATOMIC.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Une procédure stockée compilée en mode natif doit contenir un bloc ATOMIC. Exemple :  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N’us_english’)  
```  
  
Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a> Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
