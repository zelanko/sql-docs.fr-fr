---
title: Types CLR définis par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: 2078b11b44232b44e94191c07fca91998f2c1172
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028349"
---
# <a name="clr-user-defined-types"></a>Types CLR définis par l'utilisateur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vous donne la possibilité de créer des objets de base de données qui sont programmés sur un assembly créé dans le common language runtime .NET Framework (CLR). Les objets de base de données pouvant tirer parti du modèle de programmation évolué fourni par le CLR comprennent les déclencheurs, les procédures stockées, les fonctions, les fonctions d'agrégation et les types.  
  
> [!NOTE]  
>  La possibilité d’exécuter du code CLR est désactivée (OFF [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) par défaut dans. Le CLR peut être activé à l’aide de la procédure stockée système **sp_configure** .  
  
 À partir [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]de, vous pouvez utiliser des types définis par l’utilisateur (UDT) pour étendre le système de type scalaire du serveur, permettant ainsi le stockage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’objets CLR dans une base de données. Les types UDT peuvent contenir plusieurs éléments et avoir des comportements, ce qui les différencie des types de données alias traditionnels qui se composent d'un seul type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les types UDT étant accessibles au système dans son ensemble, leur utilisation pour des types de données complexes peut nuire aux performances. Les données complexes sont généralement mieux modélisées au moyen de lignes et de tables traditionnelles. Les types UDT dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont bien adaptés aux éléments suivants :  
  
-   Date, heure, devise et types numériques étendus  
  
-   Applications géographiques  
  
-   Données encodées ou chiffrées  
  
 Le processus de développement de types UDT dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprend les étapes suivantes :  
  
1.  **Coder et générer l'assembly définissant le type UDT.** Les UDT sont définis à l’aide de l’un des langages pris en charge par the.NET Framework common language runtime (CLR) qui produisent du code vérifiable. notamment Visual C# et Visual Basic .NET. Les données sont exposées en tant que champs et propriétés d'une classe ou d'une structure .NET Framework, et les comportements sont définis par des méthodes de la classe ou de la structure.  
  
2.  **Inscrire l'assembly.** Les types UDT peuvent être déployés par l'intermédiaire de l'interface utilisateur Visual Studio dans un projet de base de données, ou à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY, qui copie l'assembly contenant la classe ou la structure dans une base de données.  
  
3.  **Créer le type UDT dans SQL Server.** Une fois qu'un assembly est chargé dans une base de données hôte, vous utilisez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE pour créer un type UDT et exposer les membres de la classe ou de la structure en tant que membres du type UDT. Les types UDT existent uniquement dans le contexte d'une base de données unique et, une fois inscrits, n'ont pas de dépendances vis-à-vis des fichiers externes à partir desquels ils ont été créés.  
  
    > [!NOTE]  
    >  Dans les versions antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les types UDT créés à partir d'assemblys .NET Framework n'étaient pas pris en charge. Toutefois, vous pouvez toujours utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les types de données d’alias à l’aide de **sp_addtype**. La syntaxe CREATE TYPE peut être utilisée pour créer à la fois des types de données définis par l'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] natifs et des types UDT.  
  
4.  **Créer des tables, des variables ou des paramètres à l’aide de l’UDT** À [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]partir de, un type défini par l’utilisateur peut être utilisé comme définition de colonne d’une table, en tant que [!INCLUDE[tsql](../../includes/tsql-md.md)] variable dans un lot ou en tant qu' [!INCLUDE[tsql](../../includes/tsql-md.md)] argument d’une fonction ou d’une procédure stockée.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
 Décrit comment créer des types UDT.  
  
 [Inscription des types définis par l'utilisateur dans SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/registering-user-defined-types-in-sql-server.md)  
 Décrit comment inscrire et gérer des types UDT dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Utilisation de types définis par l'utilisateur dans SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
 Décrit comment créer des requêtes à l'aide de types UDT.  
  
 [Accès aux types définis par l'utilisateur dans ADO.NET](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
 Décrit comment utiliser des types UDT à l'aide du fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans ADO.NET.  
  
  
