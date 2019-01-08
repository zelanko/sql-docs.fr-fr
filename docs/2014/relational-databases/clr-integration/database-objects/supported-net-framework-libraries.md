---
title: Prise en charge des bibliothèques .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c2518404830577839bce3e84c4eac9b76c850cd3
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53367921"
---
# <a name="supported-net-framework-libraries"></a>Bibliothèques .NET Framework prises en charge
  Avec le CLR (Common Language Runtime) hébergé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous pouvez créer des procédures stockées, des déclencheurs, des fonctions définies par l'utilisateur, des types définis par l'utilisateur et des agrégats définis par l'utilisateur en code managé. Avec les fonctionnalités présentes dans les bibliothèques de classes .NET Framework, vous avez accès à des classes prégénérées qui fournissent des fonctionnalités pour la manipulation de chaînes, des opérations de mathématique avancées, l'accès au fichier, le chiffrement, etc. Ces classes sont accessibles à partir de procédures stockées managées, de types définis par l'utilisateur, de déclencheurs, de fonctions définies par l'utilisateur ou d'agrégats définis par l'utilisateur, quels qu'ils soient.  
  
> [!NOTE]  
>  Si le service ou de la mise à niveau des assemblys non pris en charge dans le global assembly cache (GAC), votre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si un assembly existe à la fois dans un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intégration du CLR. Si vous effectuez la maintenance ou mettez à niveau des assemblys dans le GAC qui sont également inscrits dans la base de données, y compris des assemblys .NET Framework non pris en charge, veillez également à effectuer la maintenance ou à mettre à niveau la copie de l'assembly à l'intérieur de vos bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec l'instruction `ALTER ASSEMBLY` Pour plus d’informations, consultez [l’article 949080 de la de la Base de connaissances](https://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Bibliothèques prises en charge  
 À partir de [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] possède une liste de bibliothèques .NET Framework prises en charge, qui ont été testés pour s’assurer qu’ils répondent aux normes de sécurité et de fiabilité pour l’interaction avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les charge directement à partir du Global Assembly Cache (GAC).  
  
 Les bibliothèques/espaces de noms pris en charge par l'intégration du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont les suivants :  
  
-   CustomMarshalers  
  
-   Microsoft.VisualBasic  
  
-   Microsoft.VisualC  
  
-   mscorlib  
  
-   Système  
  
-   System.Configuration  
  
-   System.Data  
  
-   System.Data.OracleClient  
  
-   System.Data.SqlXml  
  
-   System.Deployment  
  
-   System.Security  
  
-   System.Transactions  
  
-   System.Web.Services  
  
-   System.Xml  
  
-   System.Core.dll  
  
-   System.Xml.Linq.dll  
  
## <a name="unsupported-libraries"></a>Bibliothèques non prises en charge  
 Il est toujours possible d'appeler des bibliothèques non prises en charge à partir de vos procédures stockées managées, déclencheurs, fonctions définies par l'utilisateur, types définis par l'utilisateur et agrégats définis par l'utilisateur. Vous devez d'abord inscrire la bibliothèque non prise en charge dans la base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'instruction `CREATE ASSEMBLY` avant de pouvoir l'utiliser dans votre code. Toute bibliothèque non prise en charge qui est inscrite et exécutée sur le serveur doit être examinée et testée en termes de sécurité et de fiabilité.  
  
 Par exemple, l'espace de noms `System.DirectoryServices` n'est pas pris en charge. Vous devez inscrire l'assembly System.DirectoryServices.dll avec les autorisations `UNSAFE` avant de pouvoir l'appeler de votre code. L'autorisation `UNSAFE` est nécessaire parce que les classes dans l'espace de noms `System.DirectoryServices` ne répondent pas aux conditions requises par `SAFE` ou `EXTERNAL_ACCESS`. Pour plus d’informations, consultez [Restrictions du modèle de programmation CLR Integration](clr-integration-programming-model-restrictions.md) et [sécurité d’accès du Code CLR Integration](../security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Assembly](../assemblies/creating-an-assembly.md)   
 [Sécurité d’accès du Code CLR Integration](../security/clr-integration-code-access-security.md)   
 [Restrictions du modèle de programmation de l’intégration du CLR](clr-integration-programming-model-restrictions.md)  
  
  
