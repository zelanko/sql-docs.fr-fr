---
title: Boîte de dialogue Détails de la conversion de colonne (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cd97a1bb27858b9107312f3ac32ea61ce07f415b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045606"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Boîte de dialogue Détails de la conversion de colonne (Assistant Importation et Exportation SQL Server)
  Utilisez le **colonne Détails de la Conversion** boîte de dialogue pour passer en revue les informations de conversion détaillées concernant une colonne individuelle. Ces informations de conversion incluent notamment le type de données de la colonne au niveau de la source et de la destination, ainsi que la conversion à laquelle l'Assistant procèdera. Cette page répertorie également les fichiers de mappage de type de données que l'Assistant utilise pour déterminer les conversions de type de données requises. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installe ces fichiers de mappage de type de données au cours de l'installation.  
  
 **Pour ouvrir la boîte de dialogue Détails de Conversion de colonne**  
  
1.  Sur le **vérifier le mappage de Type de données** page de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation, dans le **Table** , sélectionnez une table.  
  
2.  Dans le **mappage de type de données** , double-cliquez sur la ligne qui contient la colonne pour laquelle vous souhaitez afficher les détails de la conversion.  
  
 Pour en savoir plus sur les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour obtenir des informations sur les options de démarrage de l’Assistant, ainsi que sur les autorisations requises pour exécuter l’Assistant, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 L’objectif de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation consiste à copier des données à partir d’une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
  