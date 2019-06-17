---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69acb74bd1c50900ae4852c41b3304da7ca7c00c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62869462"
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1807|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|CANNOT_EX_LOCK|  
|Texte du message|Impossible d'obtenir un verrou exclusif sur la base de données '%.*ls'. Recommencez l'opération ultérieurement.|  
  
## <a name="explanation"></a>Explication  
 Une opération qui requérait un accès exclusif à la base de données n'a pas pu l'obtenir.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Arrêtez toutes les connexions à cette base de données ou relancez la requête ultérieurement.  
  
  
