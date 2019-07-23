---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 84f983c9b450e625fdca08c46720a1cf22e8b84c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098315"
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
