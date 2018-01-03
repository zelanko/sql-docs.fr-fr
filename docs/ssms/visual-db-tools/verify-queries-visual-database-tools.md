---
title: "Vérifier des requêtes (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b73437cb76c8132fc2045c5553387383207a7c7f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="verify-queries-visual-database-tools"></a>Vérifier des requêtes (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Pour éviter tout problème, vérifiez que la syntaxe de la requête que vous avez conçue est correcte. Cette option s’avère particulièrement utile quand vous entrez des instructions dans le [volet SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
Tenez compte des remarques suivantes lors de la vérification de requêtes :  
  
-   Une instruction peut être valide et ne pas présenter d’erreur au moment de sa vérification, sans pour autant pouvoir être représentée dans les volets **Schéma** et **Critères**.  
  
-   La vérification SQL parvient à détecter certaines erreurs SQL, mais pas toutes. Lorsqu'une requête comporte une erreur n'ayant pas été détectée au cours de la vérification SQL, la base de données détecte cette erreur lors de l'exécution de la requête.  
  
-   Les requêtes contenant des paramètres ne peuvent pas être vérifiées.  
  
### <a name="to-verify-an-sql-statement"></a>Pour vérifier une instruction SQL  
  
-   Cliquez avec le bouton droit sur le **Volet SQL**, puis sélectionnez **Vérifier la syntaxe SQL** dans le menu contextuel.  
  
## <a name="see-also"></a> Voir aussi  
[Exécuter des requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
