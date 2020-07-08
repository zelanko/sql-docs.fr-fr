---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 18c8e591f255b57f8cbb935075695fca7bcc3960
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637061"
---
# <a name="mssqlserver_8689"></a>MSSQLSERVER_8689
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|8689|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|USEPLAN_ERR_NO_DB|  
|Texte du message|La base de données '%.*ls' spécifiée dans l'indicateur USE PLAN n'existe pas. Indiquez une base de données existante.|  
  
## <a name="explanation"></a>Explication  
Une base de données spécifiée dans l'indicateur USE PLAN n'existe pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Veillez à ce que toutes les bases de données spécifiées dans l'indicateur USE PLAN existent.  
  
## <a name="see-also"></a>Voir aussi  
[Indicateurs de requête &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
  
