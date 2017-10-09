---
title: "RÉVOQUER les autorisations de Collection de schémas XML (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, XML schema collections
- XML schema collections [SQL Server], permissions
- schema collections [SQL Server], permissions
ms.assetid: 8ca0973c-30b2-4633-a165-c09b13cc81ae
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4d7d530e89bdd3dcb320c4a08c340071b7faba3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-xml-schema-collection-permissions-transact-sql"></a>REVOKE – révocation d'autorisations de collection de schémas XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Révoque des autorisations octroyées ou refusées sur une collection de schémas XML.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] ON   
    XML SCHEMA COLLECTION :: [ schema_name . ]  
    XML_schema_collection_name  
    { TO | FROM } <database_principal> [ ,...n ]  
        [ CASCADE ]  
    [ AS <database_principal> ]   
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qui peut être révoquée sur une collection de schémas XML. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 COLLECTION de schémas XML ON :: [ *nom_schéma***.** ] *XML_schema_collection_name*  
 Spécifie la collection de schémas XML sur laquelle l'autorisation doit être révoquée. L'identificateur d'étendue (::) est requis. Si *nom_schéma* n’est pas spécifié, le schéma par défaut est utilisé. Si *schema_name* est spécifié, le qualificateur d’étendue de schéma (.) est requis.  
  
 GRANT OPTION  
 Indique que le droit d'accorder l'autorisation spécifiée à d'autres principaux sera révoqué. L'autorisation elle-même ne sera pas révoquée.  
  
> [!IMPORTANT]  
>  Si le principal possède l'autorisation spécifiée sans l'option GRANT, l'autorisation elle-même sera révoquée.  
  
 CASCADE  
 Indique que l'autorisation en cours de révocation est également révoquée sur les principaux auxquels cette autorisation a été accordée ou révoquée par ce principal.  
  
> [!CAUTION]  
>  Une révocation en cascade d'une autorisation accordée avec l'option WITH GRANT OPTION entraîne la révocation des deux options GRANT et DENY de cette autorisation.  
  
 {POUR | FROM} \< *principal_base_de_données*>  
 Spécifie le principal pour lequel l'autorisation est révoquée.  
  
 En tant que \<principal_base_de_données > Spécifie un principal à partir duquel le principal qui exécute cette requête dérive son droit de révoquer l’autorisation.  
  
 *Database_user*  
 Spécifie un utilisateur de base de données.  
  
 *Database_role*  
 Spécifie un rôle de base de données.  
  
 *Application_role*  
 Spécifie un rôle d'application.  
  
 *Database_user_mapped_to_Windows_User*  
 Spécifie un utilisateur de base de données mappé sur un utilisateur Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Spécifie un utilisateur de base de données mappé à un groupe Windows.  
  
 *Database_user_mapped_to_certificate*  
 Spécifie un utilisateur de base de données mappé sur un certificat.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Spécifie un utilisateur de base de données mappé à une clé asymétrique.  
  
 *Database_user_with_no_login*  
 Spécifie un utilisateur de base de données sans principal au niveau serveur correspondant.  
  
## <a name="remarks"></a>Notes  
 Informations sur les collections de schémas XML sont visibles dans le [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) affichage catalogue.  
  
 L'instruction échoue si l'option CASCADE n'est pas spécifiée lorsque vous révoquez une autorisation à partir d'un principal auquel cette autorisation a été accordée avec l'option GRANT OPTION.  
  
 Une collection de schémas XML est un élément sécurisable de niveau schéma inclus dans le schéma qui est son parent dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qu'il est possible de révoquer sur une collection de schémas XML sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation de collection de schémas XML|Déduite d'une autorisation de collection de schémas XML|Déduite d'une autorisation de schéma|  
|--------------------------------------|-------------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|Exécutez|CONTROL|Exécutez|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Requiert l’autorisation CONTROL sur la collection de schémas XML. Si vous utilisez l'option AS, le principal spécifié doit posséder la collection de schémas XML.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, l'autorisation `EXECUTE` sur la collection de schémas XML `Invoices4` est révoquée pour l'utilisateur `Wanida`. La collection de schémas XML `Invoices4` se trouve à l'intérieur du schéma `Sales` de la base de données `AdventureWorks2012`.  
  
 ```
 USE AdventureWorks2012;  
 REVOKE EXECUTE ON XML SCHEMA COLLECTION::Sales.Invoices4 FROM Wanida;  
 GO
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [ACCORDER des autorisations de Collection de schémas XML &#40; Transact-SQL &#41;](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)   
 [REFUSER des autorisations de Collection de schémas XML &#40; Transact-SQL &#41;](../../t-sql/statements/deny-xml-schema-collection-permissions-transact-sql.md)   
 [Sys.xml_schema_collections &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)   
 [CRÉER une COLLECTION de schémas XML &#40; Transact-SQL &#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


