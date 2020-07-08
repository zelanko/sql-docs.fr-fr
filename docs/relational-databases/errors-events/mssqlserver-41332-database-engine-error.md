---
title: MSSQLSERVER_41332 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a0ae51ca0aea57f454446301f0e624298f146e5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85694275"
---
# <a name="mssqlserver_41332"></a>MSSQLSERVER_41332
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41332|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQL_SNAPSHOT_NOT_SUPPORTED|  
|Texte du message|Les tables optimisées en mémoire et les procédures stockées compilées en mode natif ne sont pas accessibles ou ne peuvent pas être créées lorsque la session TRANSACTION ISOLATION LEVEL a la valeur SNAPSHOT.|  
  
## <a name="explanation"></a>Explication  
La transaction a démarré au niveau d'isolation SNAPSHOT, puis a tenté d'utiliser une fonctionnalité qui n'est pas compatible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Démarrer la transaction avec un autre niveau d'isolation. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
