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
ms.openlocfilehash: a2981d59b8bcc21d9a21fe0fd707cfcb9278cc57
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717006"
---
# <a name="mssqlserver_5245"></a>MSSQLSERVER_5245
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|5245|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Texte du message|ID d’objet O_ID (objet 'NAME') : DBCC n’a pas pu obtenir de verrou pour cet objet, car le délai d’attente de la requête de verrouillage a été dépassé. Cet objet a été ignoré et il ne sera pas traité.|  
  
## <a name="explanation"></a>Explication  
Le délai d'attente de verrouillage a expiré pendant que DBCC attendait un verrouillage de table pour l'objet spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez de nouveau la commande DBCC.  
  
