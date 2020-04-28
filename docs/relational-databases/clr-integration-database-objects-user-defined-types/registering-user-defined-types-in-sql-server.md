---
title: Inscription de types définis par l’utilisateur dans SQL Server | Microsoft Docs
description: Vous devez inscrire un UDT avant de l’installer dans SQL Server. Vous devez inscrire l’assembly et créer le type dans la base de données où vous souhaitez l’utiliser.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [CLR integration], maintaining
- user-defined types [CLR integration], maintaining
- dependencies [CLR integration]
- deploying user-defined types [CLR integration]
- CurrencyConversion function
- user-defined types [CLR integration], deploying
- Transact-SQL deploying UDTs
- assemblies [CLR integration], user-defined types
- cross-database UDT support
- CREATE ASSEMBLY statement
- DROP TYPE statement
- Currency UDT
- CREATE TYPE statement
- registering user-defined types
- UDTs [CLR integration], deploying
- removing user-defined types
- user-defined types [CLR integration], registering
- ALTER ASSEMBLY statement
- UDTs [CLR integration], registering
- ADD FILE clause
ms.assetid: f7da3e92-e407-4f0b-b3a3-f214e442b37d
author: rothja
ms.author: jroth
ms.openlocfilehash: e4383e245048035d4c05f7be3bedb7d3d13f835d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81486927"
---
# <a name="registering-user-defined-types-in-sql-server"></a>Inscription des types définis par l'utilisateur dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Pour pouvoir utiliser un type défini par l’utilisateur (UDT) dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez l’inscrire. L'inscription d'un UDT comprend l'inscription de l'assembly et la création du type dans la base de données dans laquelle vous souhaitez l'utiliser. La portée des UDT se limite à une seule base de données. Ils ne peuvent pas être utilisés dans plusieurs bases de données à moins d'inscrire le même assembly et UDT dans chaque base de données. Une fois l'assembly de l'UDT inscrit et le type créé, vous pouvez utiliser l'UDT dans [!INCLUDE[tsql](../../includes/tsql-md.md)] et dans le code client. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="using-visual-studio-to-deploy-udts"></a>Utilisation de Visual Studio pour déployer des UDT  
 Le moyen le plus simple de déployer votre UDT consiste à utiliser [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio. Toutefois, dans des scénarios de déploiement plus complexes et pour une souplesse maximale, utilisez [!INCLUDE[tsql](../../includes/tsql-md.md)] comme discuté plus loin dans cette rubrique.  
  
 Procédez comme suit pour créer et déployer un UDT à l'aide de Visual Studio :  
  
1.  Créez un projet **de base de données** dans les nœuds de langage **Visual Basic** ou **Visual C#** .  
  
2.  Ajoutez une référence à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contiendra l'UDT.  
  
3.  Ajoutez une classe de **type défini par l’utilisateur** .  
  
4.  Écrivez le code d'implémentation de l'UDT.  
  
5.  Dans le menu **générer** , sélectionnez **déployer**. L'assembly est alors inscrit et le type est créé dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="using-transact-sql-to-deploy-udts"></a>Utilisation de Transact-SQL pour déployer des UDT  
 Le syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY est utilisée pour inscrire l'assembly dans la base de données dans laquelle vous souhaitez utiliser l'UDT. L'assembly est stocké en interne dans les tables système de la base de données, et non en externe dans le système de fichiers. Si l'UDT est dépendant d'assemblys externes, ces derniers doivent également être chargés dans la base de données. L'instruction CREATE TYPE est utilisée pour créer l'UDT dans la base de données dans laquelle il sera utilisé. Pour plus d’informations, consultez [Create assembly &#40;Transact-sql&#41;](../../t-sql/statements/create-assembly-transact-sql.md) et [create type &#40;transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md).  
  
### <a name="using-create-assembly"></a>Utilisation de CREATE ASSEMBLY  
 Le syntaxe CREATE ASSEMBLY permet d'inscrire l'assembly dans la base de données dans laquelle vous souhaitez utiliser l'UDT. Une fois l'assembly inscrit, il n'a plus de dépendances.  
  
 La création de plusieurs versions du même assembly dans une même base de données n'est pas autorisée. Toutefois, il est possible de créer plusieurs versions du même assembly dans une même base de données en fonction de la culture. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distingue les différentes versions culturelles d'un assembly par des noms différents qui sont inscrits dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez la section relative à la création et à l'utilisation d'assemblys avec nom fort dans le Kit de développement logiciel du .NET Framework.  
  
 Lorsque CREATE ASSEMBLY est exécuté avec le jeu d'autorisations SAFE ou EXTERNAL_ACCESS, l'assembly est vérifié pour s'assurer qu'il est vérifiable et sécurisé. Si vous omettez de spécifier un jeu d'autorisations, le jeu SAFE est utilisé. Le code associé au jeu d'autorisations UNSAFE n'est pas vérifié. Pour plus d’informations sur les jeux d’autorisations des assemblys, consultez [Conception d’assemblys](../../relational-databases/clr-integration/assemblies-designing.md).  
  
#### <a name="example"></a>Exemple  
 L’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante inscrit l’assembly point dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données **ADVENTUREWORKS** , avec l’autorisation Safe définie. Si la clause WITH PERMISSION_SET est omise, l'assembly est inscrit avec le jeu d'autorisations SAFE.  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM '\\ShareName\Projects\Point\bin\Point.dll'   
WITH PERMISSION_SET = SAFE;  
```  
  
 L’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante inscrit l’assembly à l’aide de *<assembly_bits argument>* dans la clause from. Cette valeur **varbinary** représente le fichier sous la forme d’un flux d’octets.  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM 0xfeac4 ... 21ac78  
```  
  
### <a name="using-create-type"></a>Utilisation de CREATE TYPE  
 Une fois l'assembly chargé dans la base de données, vous pouvez créer le type à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE. Le type est alors ajouté à la liste des types disponibles pour cette base de données. La portée du type se limite à la base de données ; il ne peut être utilisé que dans la base de données dans laquelle il a été créé. Si l'UDT existe déjà dans la base de données, l'instruction CREATE TYPE échoue avec une erreur.  
  
> [!NOTE]  
>  La syntaxe CREATe TYPE est également utilisée pour créer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des types de données d’alias natifs, et est destinée à remplacer **sp_addtype** comme moyen de créer des types de données d’alias. Certains arguments facultatifs de la syntaxe CREATE TYPE se rapportent à la création d'UDT et ne peuvent pas être appliqués à la création de types de données d'alias.  
  
 Pour plus d’informations, consultez [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md).  
  
#### <a name="example"></a>Exemple  
 L’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante crée le type **point** . Le nom externe est spécifié à l’aide de la syntaxe de dénomination en deux parties de *AssemblyName*. *UDTName*.  
  
```  
CREATE TYPE dbo.Point   
EXTERNAL NAME Point.[Point];  
```  
  
## <a name="removing-a-udt-from-the-database"></a>Suppression d'un UDT de la base de données  
 L'instruction DROP TYPE supprime un UDT de la base de données active. Une fois un UDT supprimé, vous pouvez utiliser l'instruction DROP ASSEMBLY pour supprimer l'assembly de la base de données.  
  
 L'instruction DROP TYPE ne s'exécute pas dans les situations suivantes :  
  
-   Des tables de la base de données contiennent des colonnes définies à l'aide de l'UDT.  
  
-   Des fonctions, procédures stockées ou déclencheurs créés dans la base de données avec la clause WITH SCHEMABINDING utilisent des variables ou des paramètres de l'UDT.  
  
### <a name="example"></a>Exemple  
 L'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante doit s'exécuter dans l'ordre suivant. Tout d’abord, la table qui fait référence à l’UDT **point** doit être supprimée, puis le type et enfin l’assembly.  
  
```  
DROP TABLE dbo.Points;  
DROP TYPE dbo.Point;  
DROP ASSEMBLY Point;  
```  
  
### <a name="finding-udt-dependencies"></a>Recherche des dépendances d'un UDT  
 En présence d'objets dépendants, comme des tables avec des définitions de colonne UDT, l'instruction DROP TYPE échoue. Elle échoue également si des fonctions, procédures stockées ou déclencheurs créés dans la base de données à l'aide de la clause WITH SCHEMABINDING utilisent des variables ou des paramètres du type défini par l'utilisateur. Vous devez commencer par supprimer tous les objets dépendants, puis exécuter l'instruction DROP TYPE.  
  
 La requête [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante localise toutes les colonnes et tous les paramètres qui utilisent un UDT dans la base de données **AdventureWorks** .  
  
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
  
## <a name="maintaining-udts"></a>Maintenance des UDT  
 Vous ne pouvez pas modifier un UDT qui a été créé dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez toutefois modifier l'assembly sur lequel repose ce type. Dans la plupart des cas, vous devez supprimer l'UDT de la base de données à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE, apporter des modifications à l'assembly sous-jacent et le recharger à l'aide de l'instruction ALTER ASSEMBLY. Vous devez ensuite recréer l'UDT et tout objet dépendant.  
  
### <a name="example"></a>Exemple  
 L'instruction ALTER ASSEMBLY est utilisée une fois que vous avez modifié le code source dans votre assembly UDT et l'avez recompilé. Elle copie le fichier .dll sur le serveur et le lie au nouvel assembly. Pour obtenir la syntaxe complète, consultez [ALTER assembly &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md).  
  
 L'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY suivante recharge l'assembly Point.dll à partir de l'emplacement spécifié sur le disque.  
  
```  
ALTER ASSEMBLY Point  
FROM '\\Projects\Point\bin\Point.dll'  
```  
  
### <a name="using-alter-assembly-to-add-source-code"></a>Utilisation de l'instruction ALTER ASSEMBLY pour ajouter le code source  
 La clause ADD FILE de la syntaxe ALTER ASSEMBLY n'est pas présente dans CREATE ASSEMBLY. Vous pouvez l'utiliser pour ajouter le code source ou tout autre fichier associé à un assembly. Les fichiers sont copiés depuis leur emplacement d'origine et stockés dans les tables système de la base de données. Le code source et autres fichiers est toujours à portée de main dans l'éventualité où vous deviez recréer ou documenter la version actuelle de l'UDT.  
  
 L’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER assembly suivante ajoute le code source de la classe point.cs pour le type UDT **point** . Le texte contenu dans le fichier Point.cs est alors copié et stocké dans la base de données sous le nom PointSource.  
  
```  
ALTER ASSEMBLY Point  
ADD FILE FROM '\\Projects\Point\Point.cs' AS PointSource;  
```  
  
 Les informations d’assembly sont stockées dans la table **sys. assembly_files** de la base de données dans laquelle l’assembly a été installé. La table **sys. assembly_files** contient les colonnes suivantes.  
  
 **assembly_id**  
 Identificateur défini pour l'assembly. Ce numéro est affecté à tous les objets se rapportant au même assembly.  
  
 **name**  
 Nom de l'objet.  
  
 **file_id**  
 Nombre identifiant chaque objet, avec le premier objet associé à un **assembly_id** donné qui reçoit la valeur 1. Si plusieurs objets sont associés au même **assembly_id**, chaque valeur de **file_id** suivante est incrémentée de 1.  
  
 **content**  
 Représentation hexadécimale de l'assembly ou du fichier.  
  
 Vous pouvez utiliser la fonction CAST ou CONVERT pour convertir le contenu de la colonne de **contenu** en texte lisible. La requête suivante convertit le contenu du fichier Point.cs en texte lisible, en utilisant le nom indiqué dans la clause WHERE pour limiter le jeu de résultats à une ligne unique.  
  
```  
SELECT CAST(content AS varchar(8000))   
  FROM sys.assembly_files   
  WHERE name='PointSource';  
```  
  
 Si vous copiez et collez les résultats dans un éditeur de texte, vous pouvez constater que les sauts de ligne et les espaces qui existaient dans l'original ont été conservés.  
  
## <a name="managing-udts-and-assemblies"></a>Gestion des UDT et des assemblys  
 Lors de la planification de votre implémentation d'UDT, identifiez les méthodes qui sont nécessaires dans l'assembly lui-même de l'UDT, ainsi que celles qui doivent être créées dans des assemblys distincts et implémentées en tant que fonctions définies par l'utilisateur ou procédures stockées. Le fait de séparer les méthodes dans des assemblys distincts vous permet de mettre à jour le code sans affecter les données qui peuvent être stockées dans une colonne UDT d'une table. Vous pouvez modifier les assemblys d'UDT sans supprimer de colonnes UDT et autres objets dépendants uniquement lorsque la nouvelle définition peut lire les valeurs précédentes et que la signature du type ne change pas.  
  
 Le fait de séparer le code de procédure susceptible de changer du code requis pour implémenter l'UDT simplifie considérablement la maintenance. Par ailleurs, le fait de n'inclure que le code qui est nécessaire au fonctionnement de l'UDT et de créer des définitions d'UDT aussi simples que possible réduit le risque que l'UDT lui-même ait besoin d'être supprimé de la base de données pour les révisions de code ou la résolution de bogues.  
  
### <a name="the-currency-udt-and-currency-conversion-function"></a>UDT Currency et fonction de conversion de devise  
 L’UDT **Currency** de l’exemple de base de données **AdventureWorks** fournit un exemple utile de la méthode recommandée pour structurer un UDT et ses fonctions associées. Le type défini par l’utilisateur **Currency** est utilisé pour gérer les données financières en fonction du système monétaire d’une culture particulière, et permet de stocker différents types de devises, tels que des dollars, des euros, etc. La classe UDT expose un nom de culture sous forme de chaîne et une somme d’argent sous la forme d’un type de données **décimal** . Toutes les méthodes de sérialisation nécessaires sont contenues dans l'assembly qui définit la classe. La fonction qui implémente la conversion monétaire d’une culture à une autre est implémentée en tant que fonction externe nommée **ConvertCurrency**, et cette fonction se trouve dans un assembly distinct. La fonction **ConvertCurrency** effectue son travail en extrayant le taux de conversion d’une table de la base de données **AdventureWorks** . Si la source des taux de conversion doit être modifiée ou si d’autres modifications doivent être apportées au code existant, l’assembly peut être facilement modifié sans affecter l’UDT **Currency** .  
  
 Vous pouvez trouver le code de l’UDT **Currency** et des fonctions **ConvertCurrency** en installant les exemples de Common Language Runtime (CLR).  
  
### <a name="using-udts-across-databases"></a>Utilisation d'UDT dans plusieurs bases de données  
 Par définition, la portée des UDT se limite à une seule base de données. Autrement dit, un UDT défini dans une base de données ne peut pas être utilisé dans une définition de colonne d'une autre base de données. Pour utiliser des UDT dans plusieurs bases de données, vous devez exécuter les instructions CREATE ASSEMBLY et CREATE TYPE dans chaque base de données sur des assemblys identiques. Les assemblys sont considérés comme identiques s'ils partagent les mêmes nom, nom fort, culture, version, jeu d'autorisations et contenu binaire.  
  
 Une fois l'UDT inscrit et accessible dans les deux bases de données, vous pouvez convertir une valeur UDT d'une base de données en vue de l'utiliser dans une autre. Des UDT identiques peuvent être utilisés dans plusieurs bases de données dans les scénarios suivants :  
  
-   appel de procédures stockées définies dans des base de données différentes ;  
  
-   interrogation de tables définies dans des bases de données différentes ;  
  
-   sélection de données UDT dans une colonne UDT de table de base de données et insertion dans une seconde base de données avec une colonne UDT identique.  
  
 Dans ces situations, toute conversion requise par le serveur se produit automatiquement. Vous ne pouvez pas effectuer explicitement ces conversions à l'aide des fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST ou CONVERT.  
  
 Notez que vous n’avez pas besoin d’effectuer d’action pour utiliser des [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] UDT lorsque crée des tables de travail dans la base de données système **tempdb** . Cela inclut la gestion des curseurs, des variables de table et des fonctions table définies par l’utilisateur qui incluent des UDT et qui utilisent **tempdb**de manière transparente. Toutefois, si vous créez explicitement une table temporaire dans **tempdb** qui définit une colonne UDT, le type défini par l’utilisateur doit être inscrit dans **tempdb** de la même façon que pour une base de données utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Types CLR définis par l'utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
