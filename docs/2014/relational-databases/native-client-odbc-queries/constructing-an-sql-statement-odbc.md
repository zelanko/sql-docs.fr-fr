---
title: Construction d’une instruction SQL (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30d3f6bee83b24bd95e95aa1862a179152db0b39
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429708"
---
# <a name="constructing-an-sql-statement-odbc"></a>Construction d'une instruction SQL (ODBC)
  Les applications ODBC effectuent la plus grande partie de leur accès aux bases de données en exécutant des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. La forme de ces instructions dépend des spécifications d'application. Les instructions SQL peuvent être construites des manières suivantes :  
  
-   Codées de manière irréversible  
  
     Instructions statiques exécutées par une application en tant que tâche fixe.  
  
-   Construction au moment de l'exécution  
  
     Les instructions SQL construites au moment de l'exécution permettent à l'utilisateur de personnaliser l'instruction en utilisant des clauses courantes telles que SELECT, WHERE et ORDER BY. Cela inclut les requêtes ad hoc entrées par les utilisateurs.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC du Client analyse les instructions SQL uniquement pour la syntaxe ODBC et ISO pas directement pris en charge par le [!INCLUDE[ssDE](../../includes/ssde-md.md)], dont le pilote transforme en [!INCLUDE[tsql](../../includes/tsql-md.md)]. Toute autre syntaxe SQL est passée au [!INCLUDE[ssDE](../../includes/ssde-md.md)] inchangée, où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] déterminera s'il s'agit de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide. Cette approche fournit deux avantages :  
  
-   Réduction des coûts  
  
     Les coûts de traitement pour le pilote sont réduits car il doit analyser seulement un petit ensemble de clauses ODBC et ISO.  
  
-   Souplesse  
  
     Les programmeurs peuvent personnaliser la portabilité de leurs applications. Pour améliorer la portabilité contre plusieurs bases de données, utilisez principalement la syntaxe ODBC et ISO. Pour utiliser des améliorations spécifiques à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] appropriée. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge l’ensemble [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe pour les applications ODBC peuvent tirer parti de toutes les fonctionnalités dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La liste de colonnes dans une instruction SELECT doit contenir uniquement les colonnes requises pour effectuer la tâche actuelle. Cela réduit non seulement la quantité de données envoyées sur le réseau, mais réduit également l'impact des modifications de base de données sur l'application. Si une application ne fait pas référence à une colonne d'une table, elle n'est pas affectée par les modifications apportées à cette colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution de requêtes &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
