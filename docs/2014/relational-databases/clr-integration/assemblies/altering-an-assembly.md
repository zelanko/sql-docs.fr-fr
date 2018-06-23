---
title: Modification d’un Assembly | Documents Microsoft
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
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c4bfe1ce30b77f8c0afff3db00dd95f9f36e5ca0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045591"
---
# <a name="altering-an-assembly"></a>Modification d'un assembly
  Les assemblys inscrits dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent être mis à jour à partir d'une version plus récente via l'instruction ALTER ASSEMBLY. Pour mettre à jour un assembly, utilisez l'instruction ALTER ASSEMBLY avec la syntaxe suivante :  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 ALTER ASSEMBLY n'interrompt pas les processus en cours d'exécution qui utilisent l'assembly ; ces processus continuent à s'exécuter avec l'assembly non modifié. ALTER ASSEMBLY ne peut pas être utilisé pour modifier les signatures des fonctions CLR (Common Language Runtime), des fonctions d'agrégation, des procédures stockées et des déclencheurs. De nouvelles méthodes publiques peuvent être ajoutées à l'assembly, les méthodes privées peuvent être modifiées librement ; par ailleurs, les méthodes publiques peuvent être modifiées à condition que les signatures ou les attributs ne soient pas modifiés. Les champs qui se trouvent dans un type défini par l'utilisateur sérialisé de façon native (notamment les membres de données ou les classes de base) ne peuvent pas être modifiés via ALTER ASSEMBLY. Aucune autre modification n'est prise en charge. Pour plus d’informations, consultez [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Modification du jeu d'autorisations d'un assembly  
 Le jeu d'autorisations d'un assembly peut également être modifié à l'aide de l'instruction ALTER ASSEMBLY. L'instruction suivante modifie le jeu d'autorisations de l'assembly SQLCLRTest en le remplaçant par `EXTERNAL_ACCESS`.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Si le jeu d'autorisations d'un assembly est modifié de `SAFE` à `EXTERNAL_ACCESS` ou `UNSAFE`, une clé asymétrique et la connexion correspondante avec l'autorisation `EXTERNAL ACCESS ASSEMBLY` ou l'autorisation `UNSAFE ASSEMBLY` pour l'assembly doit être créée au préalable. Pour plus d’informations, consultez [Creating an Assembly](creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Ajout du code source d'un assembly  
 La clause ADD FILE de la syntaxe ALTER ASSEMBLY n'est pas présente dans CREATE ASSEMBLY. Vous pouvez l'utiliser pour ajouter le code source ou tout autre fichier associé à un assembly. Les fichiers sont copiés depuis leur emplacement d'origine et stockés dans les tables système de la base de données. Le code source et autres fichiers est toujours à portée de main dans l'éventualité où vous deviez recréer ou documenter la version actuelle de l'UDT.  
  
 L'instruction suivante ajoute le code source de la classe Point.cs pour le type défini par l'utilisateur Point. Le texte contenu dans le fichier Point.cs est alors copié et stocké dans la base de données sous le nom PointSource.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys d’intégration du CLR](managing-clr-integration-assemblies.md)   
 [Création d’un Assembly](creating-an-assembly.md)   
 [Suppression d’un Assembly](dropping-an-assembly.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
  
