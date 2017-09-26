---
title: "Catalog.create_environment_variable (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 91ed017b-6567-4bf2-b9f1-e2b5c70a5343
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 62aa7f67d7c7b33ac61d63b10fe45d604029500b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateenvironmentvariable-ssisdb-database"></a>catalog.create_environment_variable (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crée une variable d'environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
create_environment_variable [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @variable_name = ] variable_name  
    , [ @data_type = ] data_type  
    , [ @sensitive = ] sensitive  
    , [ @value = ] value  
    , [ @description = ] description  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient l'environnement. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @environment_name =] *environment_name*  
 Nom de l'environnement. Le *environment_name* est **nvarchar (128)**.  
  
 [ @variable_name =] *nom_variable*  
 Nom de la variable d'environnement. Le *nom_variable* est **nvarchar (128)**.  
  
 [ @data_type =] *data_type*  
 Type de données de la variable. Prise en charge des données de variable d’environnement types incluent **booléenne**, **octets**, **DateTime**, **Double**, **Int16**, **Int32**, **Int64**, **unique**, **chaîne**, **UInt32**, et **UInt64**. Types de données de la variable d’environnement non pris en charge incluent **Char**, **DBNull**, **objet**, et **Sbyte**. Type de données de la *data_type* paramètre est **nvarchar (128)**.  
  
 [ @sensitive =] *sensibles*  
 Indique si la variable contient une valeur sensible ou pas. Utilisez une valeur de `1` pour indiquer que la valeur de la variable d'environnement est sensible ou une valeur de `0` pour indiquer qu'elle n'est pas sensible. Une valeur sensible est chiffrée lorsqu'elle est stockée. Une valeur qui n’est pas sensible est stockée en texte clair. *Sensibles* est **bits**.  
  
 [ @value =] *valeur*  
 Valeur de la variable d'environnement. Le *valeur* est **sql_variant**.  
  
 [ @description =] *description*  
 Description de la variable d'environnement. Le *valeur* est **nvarchar (1024)**.  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'environnement  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le nom du dossier, le nom de l'environnement ou la variable d'environnement n'est pas valide  
  
-   Le nom de variable existe déjà dans l'environnement  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
## <a name="remarks"></a>Notes  
 Une variable d'environnement peut être utilisée pour affecter efficacement une valeur à un paramètre du projet ouà  un paramètre du package pour une utilisation dans l'exécution d'un package. Les variables d'environnement permettent d'organiser les valeurs de paramètre. Les noms de variable doivent être uniques dans un environnement.  
  
 La procédure stockée valide le type de données de la variable pour s'assurer qu'elle est prise en charge par le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
> [!TIP]  
>  Envisagez d’utiliser le **Int16** de type de données dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] au lieu de la non prise en charge **Sbyte** type de données.  
  
 La valeur passée à cette procédure stockée avec la *valeur* paramètre sera converti d’une [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] type de données à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données conformément au tableau suivant :  
  
|Type de données Integration Services|Type de données de SQL Server|  
|------------------------------------|--------------------------|  
|**Booléen**|**bit**|  
|**Octets**|**binaire**, **varbinary**|  
|**DateTime**|**DateTime**, **datetime2**, **datetimeoffset**, **smalldatetime**|  
|**Double**|Valeur numérique exacte : **décimal**, **numérique**; Numérique approché : **float**, **réel**|  
|**Int16**|**smallint**|  
|**Int32**|**int**|  
|**Int64**|**bigint**|  
|**Unique**|Valeur numérique exacte : **décimal**, **numérique**; Numérique approché : **float**, **réel**|  
|**Chaîne**|**varchar**, **nvarchar**, **char**|  
|**UInt32**|**int** (c’est le mappage le plus proche pour **Uint32**.)|  
|**UInt64**|**bigint** (c’est le mappage le plus proche pour **Uint64**.)|  
  
  
