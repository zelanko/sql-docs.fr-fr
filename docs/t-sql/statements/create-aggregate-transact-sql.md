---
title: "Créez l’agrégat (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_AGGREGATE_TSQL
- CREATE AGGREGATE
- AGGREGATE_TSQL
- AGGREGATE
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE AGGREGATE statement
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: 62eebc19-9f15-4245-94fa-b3fcd64a9d42
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07509e36b76aad995297cfae0147df7e8db41c20
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="create-aggregate-transact-sql"></a>CREATE AGGREGATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une fonction d'agrégation définie par l'utilisateur dont l'implémentation est définie dans une classe d'un assembly dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour lier la fonction d’agrégation à son implémentation, la [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assembly qui contient l’implémentation doit d’abord être téléchargé dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une instruction CREATE ASSEMBLY.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE AGGREGATE [ schema_name . ] aggregate_name  
        (@param_name <input_sqltype>   
        [ ,...n ] )  
RETURNS <return_sqltype>  
EXTERNAL NAME assembly_name [ .class_name ]  
  
<input_sqltype> ::=  
        system_scalar_type | { [ udt_schema_name. ] udt_type_name }  
  
<return_sqltype> ::=  
        system_scalar_type | { [ udt_schema_name. ] udt_type_name }  
  
```  
  
## <a name="arguments"></a>Arguments  
 *schema_name*  
 Nom du schéma auquel appartient la fonction d'agrégation définie par l'utilisateur.  
  
 *aggregate_name*  
 Nom de la fonction d'agrégation que vous voulez créer.  
  
 **@** *param_name*  
 Un ou plusieurs paramètres dans l'agrégat défini par l'utilisateur. L'utilisateur doit fournir la valeur d'un paramètre lors de l'exécution de la fonction d'agrégation. Spécifiez un nom de paramètre à l’aide d’un signe « at » (**@**) comme premier caractère. Le nom du paramètre doit respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md). Les paramètres sont locaux à la fonction.  
  
 *system_scalar_type*  
 Un des types de données scalaires système de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contiennent la valeur du paramètre d'entrée ou la valeur de retour. Tous les types de données scalaires peuvent être utilisés en tant que paramètre pour un agrégat défini par l’utilisateur, sauf **texte**, **ntext**, et **image**. Types non scalaires, tels que **curseur** et **table**, ne peut pas être spécifié.  
  
 *udt_schema_name*  
 Nom du schéma auquel appartient le type CLR défini par l'utilisateur. Si non spécifié, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] références *udt_type_name* dans l’ordre suivant :  
  
-   l'espace de noms de type SQL natif ;  
  
-   Le schéma par défaut de l'utilisateur actuel dans la base de données active  
  
-   Schéma **dbo** dans la base de données active.  
  
 *udt_type_name*  
 Nom d'un type CLR défini par l'utilisateur et déjà créé dans la base de données active. Si *udt_schema_name* n’est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suppose que le type appartient au schéma de l’utilisateur actuel.  
  
 *assembly_name* [ **.***class_name* ]  
 Spécifie l'assembly à lier à la fonction d'agrégation définie par l'utilisateur et, éventuellement, le nom du schéma auquel appartient l'assembly et le nom de la classe d'assembly qui met en œuvre l'agrégation définie par l'utilisateur. L'assembly doit avoir été déjà créé dans la base de données à l'aide de l'instruction CREATE ASSEMBLY. *CLASS_NAME* doit être valide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificateur et mise en correspondance le nom d’une classe qui existe dans l’assembly. *CLASS_NAME* peut être un nom qualifié d’espace de noms si le langage de programmation utilisé pour écrire la classe utilise des espaces de noms, tel que c#. Si *class_name* n’est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suppose qu’il est identique *aggregate_name*.  
  
## <a name="remarks"></a>Notes  
 Par défaut, la possibilité de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'exécuter du code CLR est désactivée. Vous pouvez créer, modifier et supprimer des objets de base de données qui référencent des modules de code managé, mais le code dans ces modules ne s’exécutera pas dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sauf si le [option clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) est activé à l’aide de [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 La classe de l’assembly référencé dans *assembly_name* et ses méthodes doivent répondre à la configuration requise pour l’implémentation d’une fonction d’agrégation définie par l’utilisateur dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [les agrégats](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite les autorisations CREATE AGGREGATE et REFERENCES pour l'assembly mentionné dans la clause EXTERNAL NAME.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant suppose qu'un exemple d'application windows StringUtilities.csproj est compilé. Pour plus d’informations, consultez [exemple de fonctions de chaîne Utility](http://msdn.microsoft.com/library/9623013f-15f1-4614-8dac-1155e57c880c).  
  
 L'exemple crée une agrégation `Concatenate`. Avant la création de celle-ci, l'assembly `StringUtilities.dll` est enregistré dans la base de données locale.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
-- You may have to modify the value of the this variable if you have  
--installed the sample some location other than the default location.  
  
SELECT @SamplesPath = REPLACE(physical_name, 'Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\master.mdf', 'Microsoft SQL Server\130\Samples\Engine\Programmability\CLR\')   
     FROM master.sys.database_files   
     WHERE name = 'master';  
  
CREATE ASSEMBLY StringUtilities FROM @SamplesPath + 'StringUtilities\CS\StringUtilities\bin\debug\StringUtilities.dll'  
WITH PERMISSION_SET=SAFE;  
GO  
  
CREATE AGGREGATE Concatenate(@input nvarchar(4000))  
RETURNS nvarchar(4000)  
EXTERNAL NAME [StringUtilities].[Microsoft.Samples.SqlServer.Concatenate];  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DROP AGGREGATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-aggregate-transact-sql.md)  
  
  
