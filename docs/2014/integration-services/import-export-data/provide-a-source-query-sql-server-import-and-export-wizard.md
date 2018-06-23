---
title: Fournir une requête source (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1c8ad78723a1325ac6e21365b3e00e43f2d36d55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052207"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a>Fournir une requête source (Assistant Importation et Exportation SQL Server)
  Utilisez le **fournir une requête Source** page pour taper l’instruction SQL qui génère les données à copier à partir de la source de données vers la destination.  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que les autorisations requises pour exécuter l’Assistant, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Instruction SQL**  
 Tapez une instruction de requête pour extraire des lignes de données sélectionnées de la base de données source. Par exemple, l'instruction de requête suivante extrait les données **SalesPersonID**, **SalesQuota**et **SalesYTD** de la base de données AdventureWorks pour le personnel commercial dont le pourcentage des commissions est supérieur à 1,5 %.  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 **Analyser**  
 Vérifie la syntaxe de l’instruction SQL affichée dans la zone de texte **Instruction SQL**.  
  
> [!NOTE]  
>  Si le temps requis pour vérifier la syntaxe de l'instruction dépasse la valeur du délai d'attente de 30 secondes, l'analyse s'arrête et génère une erreur. Vous ne serez pas en mesure de dépasser cette page de l'Assistant tant que l'analyse n'aura pas réussi. Une solution consiste à créer une vue de base de données basée sur la requête, puis à interroger la vue à partir de l'Assistant, au lieu d'entrer directement le texte de requête.  
  
 **Parcourir**  
 Sélectionnez un fichier contenant une instruction SQL à l’aide de la **ouvrir** boîte de dialogue. La sélection d'un fichier copie le texte dans la zone de texte **Instruction de requête** .  
  
  