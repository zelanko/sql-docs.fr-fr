---
title: Créer des requêtes de recherche en texte intégral (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 198ffa79ab4f0e7b8874bff4f4558509d051c547
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984951"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Créer des requêtes de recherche en texte intégral (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
La recherche en texte intégral utilise le prédicat CONTAINS pour localiser les lignes contenant le texte spécifié dans une colonne donnée. Les recherches en texte intégral ne sont possibles que sur les colonnes possédant des index de texte intégral actifs. Si vous tentez d'utiliser la clause CONTAINS sur une colonne qui ne possède pas d'index de texte intégral actuellement actif, une erreur s'affiche. Pour plus d’informations sur les index de texte intégral et la clause CONTAINS, consultez [Recherche en texte intégral (SQL Server)](http://msdn.microsoft.com/a0ce315d-f96d-4e5d-b4eb-ff76811cab75) et [CONTAINS (Transact-SQL)](http://msdn.microsoft.com/996c72fc-b1ab-4c96-bd12-946be9c18f84).  
  
### <a name="to-create-a-full-text-search-query"></a>Pour créer une requête de recherche en texte intégral  
  
1.  Ouvrez une requête dans l'Explorateur de solutions ou créez-en une nouvelle.  
  
2.  Dans la clause WHERE de votre requête, utilisez la fonction CONTAINS pour rechercher une colonne de texte intégral.  
  
## <a name="see-also"></a> Voir aussi  
[Types de requêtes pris en charge &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
