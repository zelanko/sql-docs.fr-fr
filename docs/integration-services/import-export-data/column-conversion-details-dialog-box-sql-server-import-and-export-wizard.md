---
title: "Boîte de dialogue Détails de la conversion de colonne (Assistant Importation et Exportation SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d4adb7bfee3533830b3d806b666ee8866fc57bb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Boîte de dialogue Détails de la conversion de colonne (Assistant Importation et Exportation SQL Server)
  Si vous double-cliquez sur la ligne d’une colonne dans la page **Vérifier le mappage de type de données** , l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présente la boîte de dialogue **Détails de la conversion de colonne** . Dans cette page, vous pouvez passer en revue des informations de conversion détaillées pour une colonne individuelle. Ces informations comprennent les éléments suivants :
-   Le type de données de la colonne au niveau de la source et de la destination
-   La conversion du type de données que l’Assistant doit éventuellement effectuer
-   Les fichiers de mappage de type de données que l’Assistant utilise pour déterminer la conversion de type de données requise 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>Capture d’écran de la page Détails de la conversion de colonne 
 La capture d’écran suivante montre la page **Détails de la conversion de colonne** de l’Assistant une fois que l’utilisateur a double-cliqué sur une ligne dans la page **Vérifier le mappage de type de données** . Pour revenir aux informations relatives à la page **Vérifier le mappage de type de données** , consultez [Vérifier le mappage de type de données](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).
 
Dans cet exemple, vous voyez les éléments répertoriés ici.
-   La colonne `PersonID` dans la table SQL Server source est de type `int`. L’Assistant mappe ce type au type de données SQL Server Integration Services (SSIS) `DT_I4`, qui est un entier signé (4 octets), en faisant référence au fichier de mappage de type de données MSSQLToSSIS10.xml.
-   La colonne `PersonID` dans la table SQL Server de destination est également de type `int`. L’Assistant mappe ce type au même type de données SSIS.
-   L’Assistant conclut : *Cette colonne ne doit pas être convertie*.
 
  
 ![Page Conversion de colonne de l’Assistant Importation et Exportation](../../integration-services/import-export-data/media/column-conversion.png "Page Conversion de colonne de l’Assistant Importation et Exportation") 
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?  
 Une fois que vous avez passé en revue les détails de la conversion de colonne et cliqué sur **OK**, la boîte de dialogue **Détails de la conversion de colonne** vous renvoie à la page **Vérifier le mappage de type de données** . Pour plus d’informations, consultez [Vérifier le mappage de type de données](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>Voir aussi
[Mappage de type de données dans l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
