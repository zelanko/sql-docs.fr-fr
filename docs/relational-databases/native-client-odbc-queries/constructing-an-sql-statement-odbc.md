---
title: Construction d’une instruction SQL (ODBC) | Microsoft Docs
description: Découvrez comment le pilote ODBC du client SQL Server traite les instructions SQL, en analysant certains dans les instructions Transact-SQL et en passant les autres à la base de données inchangées.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0c10271b031c34e8da0c7da2bc3643f8dee95c0c
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001452"
---
# <a name="constructing-an-sql-statement-odbc"></a>Construction d'une instruction SQL (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Les applications ODBC effectuent la plus grande partie de leur accès aux bases de données en exécutant des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. La forme de ces instructions dépend des spécifications d'application. Les instructions SQL peuvent être construites des manières suivantes :  
  
-   Codées de manière irréversible  
  
     Instructions statiques exécutées par une application en tant que tâche fixe.  
  
-   Construction au moment de l'exécution  
  
     Les instructions SQL construites au moment de l'exécution permettent à l'utilisateur de personnaliser l'instruction en utilisant des clauses courantes telles que SELECT, WHERE et ORDER BY. Cela inclut les requêtes ad hoc entrées par les utilisateurs.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC du client analyse les instructions SQL uniquement pour la syntaxe ODBC et ISO non directement prise en charge par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] , que le pilote transforme [!INCLUDE[tsql](../../includes/tsql-md.md)] . Toute autre syntaxe SQL est passée au [!INCLUDE[ssDE](../../includes/ssde-md.md)] inchangée, où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] déterminera s'il s'agit de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide. Cette approche fournit deux avantages :  
  
-   Réduction des coûts  
  
     Les coûts de traitement pour le pilote sont réduits car il doit analyser seulement un petit ensemble de clauses ODBC et ISO.  
  
-   Souplesse  
  
     Les programmeurs peuvent personnaliser la portabilité de leurs applications. Pour améliorer la portabilité contre plusieurs bases de données, utilisez principalement la syntaxe ODBC et ISO. Pour utiliser des améliorations spécifiques à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] appropriée. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge la [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe complète afin que les applications basées sur ODBC puissent tirer parti de toutes les fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La liste de colonnes dans une instruction SELECT doit contenir uniquement les colonnes requises pour effectuer la tâche actuelle. Cela réduit non seulement la quantité de données envoyées sur le réseau, mais réduit également l'impact des modifications de base de données sur l'application. Si une application ne fait pas référence à une colonne d'une table, elle n'est pas affectée par les modifications apportées à cette colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
