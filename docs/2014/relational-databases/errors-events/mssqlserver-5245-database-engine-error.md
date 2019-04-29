---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 30b37236b321fc90372914f2af48a652d41fbe03
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913597"
---
# <a name="mssqlserver5245"></a>MSSQLSERVER_5245
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|5245|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Texte du message|ID d’objet O_ID (objet 'NAME') : DBCC n’a pas pu obtenir un verrou sur cet objet, car le délai de demande de verrou a été dépassé. Cet objet a été ignoré et il ne sera pas traité.|  
  
## <a name="explanation"></a>Explication  
Le délai d'attente de verrouillage a expiré pendant que DBCC attendait un verrouillage de table pour l'objet spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez de nouveau la commande DBCC.  
  
