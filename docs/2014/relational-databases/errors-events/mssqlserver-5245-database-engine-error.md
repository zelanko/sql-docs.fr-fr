---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cea5c900150a26ecde783e50b953cc4a035a8ff
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551216"
---
# <a name="mssqlserver_5245"></a>MSSQLSERVER_5245
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
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
  
  
