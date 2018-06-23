---
title: Suppression d’un Assembly | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3551d0971a90c77135ca3e74b30d3009108646c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140748"
---
# <a name="dropping-an-assembly"></a>Suppression d'un assembly
  Les assemblys inscrits dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'instruction CREATE ASSEMBLY peuvent être supprimés lorsque les fonctionnalités qu'ils fournissent ne sont plus nécessaires. La suppression d'un assembly supprime de la base de données l'assembly spécifié et tous les fichiers associés, tels que les fichiers de débogage. Pour supprimer un assembly, utilisez l'instruction DROP ASSEMBLY avec la syntaxe suivante :  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 DROP ASSEMBLY n'interfère pas avec le code en cours d'exécution qui référence l'assembly, mais après l'exécution de DROP ASSEMBLY, toute tentative d'appel du code de l'assembly échoue.  
  
 DROP ASSEMBLY retourne une erreur si l'assembly est référencé par un assembly existant de la base de données ou s'il est utilisé par des fonctions CLR (Common Language Runtime), des procédures, des déclencheurs, des types définis par l'utilisateur (UDT) ou des agrégats définis par l'utilisateur (UDA) dans la base de données active. En premier lieu, utilisez les instructions DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER et DROP TYPE pour supprimer tout objet de base de données managé contenu dans l'assembly.  
  
## <a name="removing-a-udt-from-the-database"></a>Suppression d'un UDT de la base de données  
 L'instruction DROP TYPE supprime un UDT de la base de données active. Une fois un UDT supprimé, vous pouvez utiliser l'instruction DROP ASSEMBLY pour supprimer l'assembly de la base de données.  
  
 L'instruction DROP TYPE échoue si les objets dépendent du type UDT, comme dans les situations suivantes :  
  
-   Des tables de la base de données contiennent des colonnes définies à l'aide de l'UDT.  
  
-   Des fonctions, procédures stockées ou déclencheurs créés dans la base de données avec la clause WITH SCHEMABINDING utilisent des variables ou des paramètres de l'UDT.  
  
### <a name="finding-udt-dependencies"></a>Recherche des dépendances d'un UDT  
 Vous devez commencer par supprimer tous les objets dépendants, puis exécuter l'instruction DROP TYPE. Les éléments suivants [!INCLUDE[tsql](../../../includes/tsql-md.md)] requête recherche toutes les colonnes et les paramètres qui utilisent un UDT dans la **AdventureWorks** base de données.  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;   
```  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys d’intégration du CLR](managing-clr-integration-assemblies.md)   
 [Modification d’un Assembly](altering-an-assembly.md)   
 [Création d’un Assembly](creating-an-assembly.md)   
 [DROP AGGREGATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql)   
 [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)   
 [DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)   
 [TYPE de déplacement &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-type-transact-sql)  
  
  
