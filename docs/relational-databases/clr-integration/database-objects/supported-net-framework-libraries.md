---
title: Bibliothèques de .NET Framework prises en charge | Microsoft Docs
description: Avec le CLR hébergé dans SQL Server, vous pouvez créer à l’aide des bibliothèques de classes .NET Framework prises en charge et des bibliothèques non prises en charge que vous inscrivez auprès d’une base de données.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 610dcca5103e4a819b0e6c59629ddd4d510f5469
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756349"
---
# <a name="supported-net-framework-libraries"></a>Bibliothèques .NET Framework prises en charge
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Avec le CLR (Common Language Runtime) hébergé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous pouvez créer des procédures stockées, des déclencheurs, des fonctions définies par l'utilisateur, des types définis par l'utilisateur et des agrégats définis par l'utilisateur en code managé. Avec les fonctionnalités présentes dans les bibliothèques de classes .NET Framework, vous avez accès à des classes prégénérées qui fournissent des fonctionnalités pour la manipulation de chaînes, des opérations de mathématique avancées, l'accès au fichier, le chiffrement, etc. Ces classes sont accessibles à partir de procédures stockées managées, de types définis par l'utilisateur, de déclencheurs, de fonctions définies par l'utilisateur ou d'agrégats définis par l'utilisateur, quels qu'ils soient.  
  
> [!NOTE]  
>  Si vous effectuez la maintenance ou mettez à niveau des assemblys non pris en charge dans le Global Assembly Cache (GAC), votre application [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut cesser de fonctionner. Cela est dû au fait que la maintenance ou la mise à niveau de bibliothèques dans le GAC ne met pas à jour ces assemblys dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. S'il existe un assembly dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et dans le GAC, les deux copies de l'assembly doivent être exactement les mêmes. Si ce n'est pas le cas, une erreur se produit lorsque l'assembly est utilisé par l'intégration du CLR [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si vous effectuez la mise à jour ou la mise à niveau de tous les assemblys du GAC qui sont également enregistrés dans la base de données, y compris les assemblys .NET Framework non pris en charge, assurez-vous également de traiter ou de mettre à niveau la copie de l’assembly à l’intérieur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de vos bases de données avec l’instruction **ALTER assembly** . Pour plus d’informations, consultez [l’article 949080](https://support.microsoft.com/kb/949080)de la base de connaissances.  
  
## <a name="supported-libraries"></a>Bibliothèques prises en charge  
 À compter de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge une liste de bibliothèques .NET Framework qui ont été testées pour vérifier qu'elles répondent aux normes de fiabilité et de sécurité en matière d'interaction avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Vous n'avez pas besoin d'inscrire explicitement les bibliothèques prises en charge sur le serveur avant de pouvoir les utiliser dans votre code ; [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les charge directement à partir du Global Assembly Cache (GAC).  
  
 Les bibliothèques/espaces de noms pris en charge par l'intégration du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont les suivants :  
  
-   CustomMarshalers  
-   Microsoft.VisualBasic  
-   Microsoft.VisualC  
-   mscorlib  
-   Système  
-   System.Configuration  
-   System.Core  
-   System.Data  
-   System.Data.OracleClient  
-   System.Data.SqlXml  
-   System.Deployment  
-   System.Security  
-   System.Transactions  
-   System.Web.Services  
-   System.Xml  
-   System.Xml.Linq  

<!--
Any modifications to the list above should be duplicated on the following page:
https://docs.microsoft.com/sql/relational-databases/clr-integration/assemblies-designing#supported-net-framework-assemblies
-->

## <a name="unsupported-libraries"></a>Bibliothèques non prises en charge  
 Il est toujours possible d'appeler des bibliothèques non prises en charge à partir de vos procédures stockées managées, déclencheurs, fonctions définies par l'utilisateur, types définis par l'utilisateur et agrégats définis par l'utilisateur. La bibliothèque non prise en charge doit d’abord être inscrite dans la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données, à l’aide de l’instruction **CREATe assembly** , avant de pouvoir être utilisée dans votre code. Toute bibliothèque non prise en charge qui est inscrite et exécutée sur le serveur doit être examinée et testée en termes de sécurité et de fiabilité.  
  
 Par exemple, l’espace de noms **System. DirectoryServices** n’est pas pris en charge. Vous devez inscrire l’assembly System.DirectoryServices.dll avec des autorisations **non sécurisées** avant de pouvoir l’appeler à partir de votre code. L’autorisation **unsafe** est nécessaire, car les classes de l’espace de noms **System. DirectoryServices** ne satisfont pas aux conditions requises pour **Safe** ou **EXTERNAL_ACCESS**. Pour plus d’informations, consultez [restrictions du modèle de programmation](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md) de l’intégration du CLR et sécurité d’accès du code d’intégration du [CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Sécurité d’accès du code d’intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Restrictions du modèle de programmation de l'intégration du CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
