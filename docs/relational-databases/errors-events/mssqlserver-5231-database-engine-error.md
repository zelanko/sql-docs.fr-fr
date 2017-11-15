---
title: "MSSQLSERVER_5231 | Microsoft Docs"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: d973161b3c7b7f84374f69b149e210cef4e9a2b9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|5231|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Texte du message|ID d'objet O_ID (objet 'NAME') : un blocage s'est produit lors de la tentative de verrouillage de cet objet en vue d'une vérification. Cet objet a été ignoré et il ne sera pas traité.|  
  
## <a name="explanation"></a>Explication  
Un blocage s'est produit lorsque DBCC essayait de verrouiller l'objet et DBCC a été choisi comme victime du blocage. L'objet ne sera pas traité.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Aucune  
  
