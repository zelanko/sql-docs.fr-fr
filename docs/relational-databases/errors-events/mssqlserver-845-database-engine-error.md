---
description: MSSQLSERVER_845
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 621699cbc4ad763eea84669e085ea492eb6a546f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420913"
---
# <a name="mssqlserver_845"></a>MSSQLSERVER_845
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|845|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|BUFLATCH_TIMEOUT|  
|Texte du message|Dépassement du délai lors de l'attente du type de verrou de mémoire tampon %d, page %S_PGID, ID de base de données %d.|  
  
## <a name="explanation"></a>Explication  
Un processus était en attente d’obtention d’un verrou, mais n’a pas pu se le procurer suite à l’expiration du délai. Cette situation peut se produire si une opération d'E/S prend trop de temps à s'accomplir, souvent à cause d'autres tâches qui bloquent les processus système. Dans d'autres cas, elle est due à une défaillance matérielle.  
  
## <a name="user-action"></a>Action de l'utilisateur  
L'exécution des tâches suivantes peut éviter cette erreur :  
  
-   Réduisez la charge de travail.  
  
-   Recherchez des erreurs d'E/S associées dans le journal des erreurs ou le journal des événements. Les erreurs d'E/S sont généralement liées à un disque défectueux.  
  
-   Recherchez dans le journal des erreurs les tâches improductives et d'autres erreurs critiques.  
  
-   Si des erreurs critiques telles que les assertions surviennent fréquemment, corrigez-les.  
  
Si le problème persiste, contactez le service de support technique de Microsoft.  
  
