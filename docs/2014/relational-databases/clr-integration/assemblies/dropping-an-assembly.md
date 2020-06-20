---
title: Suppression d’un assembly | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
ms.openlocfilehash: 45d02cbb57459a4c1c11330446021c32dc897353
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953799"
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
 Vous devez commencer par supprimer tous les objets dépendants, puis exécuter l'instruction DROP TYPE. La [!INCLUDE[tsql](../../../includes/tsql-md.md)] requête suivante localise toutes les colonnes et tous les paramètres qui utilisent un UDT dans la base de données **AdventureWorks** .  
  
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
 [Gestion des assemblys d’intégration du CLR](managing-clr-integration-assemblies.md)   
 [Modification d’un assembly](altering-an-assembly.md)   
 [Création d’un assembly](creating-an-assembly.md)   
 [DROP AGGREGATe &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql)   
 [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)   
 [SUPPRIMER la procédure &#40;&#41;Transact-SQL](/sql/t-sql/statements/drop-procedure-transact-sql)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)   
 [DROP TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-type-transact-sql)  
  
  
