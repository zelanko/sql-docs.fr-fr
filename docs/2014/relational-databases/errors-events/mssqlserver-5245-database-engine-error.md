---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 64a63825586a603e2938cd57d98d38d555420dd6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039057"
---
# <a name="mssqlserver5245"></a>MSSQLSERVER_5245
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|5245|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Texte du message|ID d'objet O_ID (objet 'NAME') : DBCC n'a pas pu obtenir de verrou pour cet objet, car le délai d'attente de la requête de verrouillage a été dépassé. Cet objet a été ignoré et il ne sera pas traité.|  
  
## <a name="explanation"></a>Explication  
 Le délai d'attente de verrouillage a expiré pendant que DBCC attendait un verrouillage de table pour l'objet spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez de nouveau la commande DBCC.  
  
  