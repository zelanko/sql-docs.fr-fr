---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2af9a604c511c50b542fbacd547afb3e09d7ea54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201869"
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3413|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|MARKDB|  
|Texte du message|ID base de données %d. Impossible de marquer la base de données comme suspecte. Échec de l'analyse Getnext NC sur sys.databases.database_id. Consultez les erreurs précédentes dans le journal des erreurs afin d'identifier la cause, puis corrigez tous les problèmes associés.|  
  
## <a name="explanation"></a>Explication  
 Une erreur inattendue s'est produite lors d'une tentative de marquage SUSPECT d'une base de données utilisateur dans le catalogue. L'état SUSPECT ne peut pas être persistant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez les erreurs précédentes et corrigez le problème.  
  
  
