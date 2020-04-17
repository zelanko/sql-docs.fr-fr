---
title: Modification d’une assemblée (fr) Microsoft Docs
description: Utilisez ALTER ASSEMBLY pour mettre à jour les assemblages enregistrés dans SQL Server. Vous pouvez également modifier l’ensemble d’autorisation et ajouter du code source ou d’autres fichiers pour une assemblée.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: 07fd94c855a81a8d58ac1ed4b578edf478dc77aa
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486837"
---
# <a name="altering-an-assembly"></a>Modification d'un assembly
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les assemblys inscrits dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent être mis à jour à partir d'une version plus récente via l'instruction ALTER ASSEMBLY. Pour mettre à jour un assembly, utilisez l'instruction ALTER ASSEMBLY avec la syntaxe suivante :  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 ALTER ASSEMBLY n'interrompt pas les processus en cours d'exécution qui utilisent l'assembly ; ces processus continuent à s'exécuter avec l'assembly non modifié. ALTER ASSEMBLY ne peut pas être utilisé pour modifier les signatures des fonctions CLR (Common Language Runtime), des fonctions d'agrégation, des procédures stockées et des déclencheurs. De nouvelles méthodes publiques peuvent être ajoutées à l'assembly, les méthodes privées peuvent être modifiées librement ; par ailleurs, les méthodes publiques peuvent être modifiées à condition que les signatures ou les attributs ne soient pas modifiés. Les champs qui se trouvent dans un type défini par l'utilisateur sérialisé de façon native (notamment les membres de données ou les classes de base) ne peuvent pas être modifiés via ALTER ASSEMBLY. Aucune autre modification n'est prise en charge. Pour plus d’informations, voir [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Modification du jeu d'autorisations d'un assembly  
 Le jeu d'autorisations d'un assembly peut également être modifié à l'aide de l'instruction ALTER ASSEMBLY. La déclaration suivante modifie l’ensemble d’autorisation de l’assemblage SQLCLRTest pour **EXTERNAL_ACCESS**.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Si l’ensemble d’autorisation d’un assemblage est modifié de **SAFE** à **EXTERNAL_ACCESS** ou **UNSAFE**, une clé asymétrique et une connexion correspondante avec l’autorisation **EXTERNAL ACCESS ASSEMBLY** ou l’autorisation UNSAFE **ASSEMBLY** pour l’assemblage doivent d’abord être créées. Pour plus d’informations, consultez [Creating an Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Ajout du code source d'un assembly  
 La clause ADD FILE de la syntaxe ALTER ASSEMBLY n'est pas présente dans CREATE ASSEMBLY. Vous pouvez l'utiliser pour ajouter le code source ou tout autre fichier associé à un assembly. Les fichiers sont copiés depuis leur emplacement d'origine et stockés dans les tables système de la base de données. Le code source et autres fichiers est toujours à portée de main dans l'éventualité où vous deviez recréer ou documenter la version actuelle de l'UDT.  
  
 L'instruction suivante ajoute le code source de la classe Point.cs pour le type défini par l'utilisateur Point. Le texte contenu dans le fichier Point.cs est alors copié et stocké dans la base de données sous le nom PointSource.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblées d’intégration CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Création d’une assemblée](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Abandon d’une assemblée](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  
