---
title: Vérifier des requêtes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ceb12a0510cd11c515c5398b4cc4051940720dd2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105562"
---
# <a name="verify-queries-visual-database-tools"></a>Vérifier des requêtes (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Pour éviter tout problème, vous pouvez vérifier la requête que vous avez conçue afin de vous assurer que sa syntaxe est correcte. Cette option s’avère particulièrement utile quand vous entrez des instructions dans le [volet SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
Tenez compte des remarques suivantes lors de la vérification de requêtes :  
  
-   Une instruction peut être valide et ne pas présenter d’erreur au moment de sa vérification, sans pour autant pouvoir être représentée dans les volets **Schéma** et **Critères**.  
  
-   La vérification SQL parvient à détecter certaines erreurs SQL, mais pas toutes. Lorsqu'une requête comporte une erreur n'ayant pas été détectée au cours de la vérification SQL, la base de données détecte cette erreur lors de l'exécution de la requête.  
  
-   Les requêtes contenant des paramètres ne peuvent pas être vérifiées.  
  
### <a name="to-verify-an-sql-statement"></a>Pour vérifier une instruction SQL  
  
-   Cliquez avec le bouton droit sur le **Volet SQL**, puis sélectionnez **Vérifier la syntaxe SQL** dans le menu contextuel.  
  
## <a name="see-also"></a>Voir aussi  
[Exécuter des requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
