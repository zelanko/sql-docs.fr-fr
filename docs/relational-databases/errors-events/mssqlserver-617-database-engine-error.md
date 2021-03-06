---
description: MSSQLSERVER_617
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f336f8b1d8cc6f20e259715f6396ce1f5e126d43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470921"
---
# <a name="mssqlserver_617"></a>MSSQLSERVER_617
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|617|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NODESHASH|  
|Texte du message|Le descripteur de l'ID d'objet %ld dans l'ID de base de données %d n'a pas été trouvé dans la table de hachage lors de la tentative de déhachage. Une entrée est manquante dans une table de travail. Réexécutez la requête. Si un curseur est concerné, fermez et rouvrez le curseur.|  
  
## <a name="explanation"></a>Explication  
SQL Server ne peut pas localiser la table de travail pour une entrée spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Si un curseur est impliqué, fermez et rouvrez celui-ci.  
  
2.  Réexécutez la requête.  
  
