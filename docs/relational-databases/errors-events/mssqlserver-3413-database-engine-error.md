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
ms.openlocfilehash: c4eaee578626daefb5c826f0eb1fb87e92cbae87
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723529"
---
# <a name="mssqlserver_3413"></a>MSSQLSERVER_3413
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|3413|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|MARKDB|  
|Texte du message|ID base de données %d. Impossible de marquer la base de données comme suspecte. Échec de l'analyse Getnext NC sur sys.databases.database_id. Consultez les erreurs précédentes dans le journal des erreurs afin d'identifier la cause, puis corrigez tous les problèmes associés.|  
  
## <a name="explanation"></a>Explication  
Une erreur inattendue s'est produite lors d'une tentative de marquage SUSPECT d'une base de données utilisateur dans le catalogue. L'état SUSPECT ne peut pas être persistant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Consultez les erreurs précédentes et corrigez le problème.  
  
