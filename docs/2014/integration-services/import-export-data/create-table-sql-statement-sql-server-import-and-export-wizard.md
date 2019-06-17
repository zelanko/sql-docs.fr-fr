---
title: Instruction SQL de création de table (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f541ad24e87bf5bdea9ed8b8c2523a73c81daa9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62768001"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>Instruction SQL de création de table (Assistant Importation et Exportation SQL Server)
  Utilisez le **instruction SQL Create Table** boîte de dialogue pour afficher l’instruction qui a été générée automatiquement, ou pour le modifier pour vos besoins. Si vous modifiez cette instruction, il est possible que vous deviez également apporter des modifications associées au mappage de colonnes. Vous devrez alors gérer manuellement l'instruction SQL modifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] génère une instruction CREATE TABLE par défaut basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table**. Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Instruction SQL**  
 Affiche l'instruction SQL générée automatiquement et permet sa modification.  
  
> [!NOTE]  
>  Si vous souhaitez inclure un retour chariot dans l'instruction SQL, appuyez sur CTRL+ENTRÉE. Si vous appuyez seulement sur ENTRÉE, la boîte de dialogue se referme.  
  
 **Créer automatiquement**  
 Restaurez l’instruction SQL par défaut, si vous l’avez modifiée, en cliquant sur **Créer automatiquement**.  
  
  
