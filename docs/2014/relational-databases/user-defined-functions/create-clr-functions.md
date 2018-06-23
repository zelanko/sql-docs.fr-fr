---
title: Créer des fonctions CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-udf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CLR functions [SQL Server]
- user-defined functions [SQL Server], CLR
ms.assetid: a82df075-2243-4e19-bfe1-ae6d65dabd0f
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 46858c9e7d5f05367d48dc55bce8ea29b22f8f2a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039251"
---
# <a name="create-clr-functions"></a>Créer des fonctions CLR
  Vous pouvez créer un objet de base de données dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programmée dans un assembly créé dans le CLR (Common Language Runtime) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Les objets de base de données peuvent exploiter le modèle de programmation élaboré fourni par les fonctions agrégées, les fonctions, les procédures stockées, les déclencheurs et les types du CLR.  
  
 La création d'une fonction CLR dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprend les étapes suivantes :  
  
-   Définissez la fonction en tant que méthode statique d'une classe dans un langage reconnu par le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Pour plus d’informations sur la programmation des fonctions dans le CLR, consultez [Fonctions CLR définies par l’utilisateur](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md). Ensuite, compilez la classe pour créer un assembly dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] à l'aide du compilateur du langage approprié.  
  
-   Enregistrez l'assembly dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'instruction CREATE ASSEMBLY. Pour plus d’informations sur les assemblys dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Assemblies &#40;moteur de base de données&#41;](../clr-integration/assemblies-database-engine.md).  
  
-   Créez la fonction qui fait référence à l’assembly inscrit à l’aide de l’instruction [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) .  
  
> [!NOTE]  
>  Le déploiement d’un projet SQL Server dans [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a pour effet d’inscrire un assembly dans la base de données qui a été spécifiée pour le projet. Le déploiement du projet crée aussi les fonctions CLR dans la base de données pour toutes les méthodes annotées par l'attribut `SqlFunction`. Pour plus d’informations, consultez [Déploiement d’objets de base de données CLR](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  La fonctionnalité d'exécution du code CLR par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est désactivée par défaut. Vous pouvez créer, modifier et supprimer des objets de base de données qui font référence à des modules de code managé, mais ces références ne s’exécutent pas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si l’option [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) n’est pas activée à l’aide de [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
## <a name="accessing-external-resources"></a>Accès aux ressources externes  
 Les fonctions CLR peuvent être utilisées pour accéder à des ressources externes telles que des fichiers, des ressources réseau, des services Web et d'autres bases de données (notamment des instances distantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Pour cela, vous devez utiliser différentes classes dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], telles que `System.IO`, `System.WebServices`, `System.Sql`, etc. L'assembly qui contient ces fonctions doit être configuré au minimum avec l'autorisation EXTERNAL_ACCESS définie dans ce but. Pour plus d’informations, consultez [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql). Vous pouvez recourir au fournisseur managé Client SQL pour accéder à des instances distantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cependant, les connexions de bouclage au serveur d'origine ne sont pas gérées dans les fonctions CLR.  
  
 **Pour créer, modifier ou supprimer des assemblys dans SQL Server**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Pour créer une fonction clr**  
  
-   [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)  
  
## <a name="accessing-native-code"></a>Accès au code natif  
 Les fonctions CLR permettent d’accéder au code natif (non managé), tel que le code écrit en C ou C++, via l’utilisation de PInvoke à partir du code managé (pour plus d’informations, consultez [Appel à des fonctions natives à partir de code managé](http://go.microsoft.com/fwlink/?LinkID=181929) ). Vous pouvez ainsi réutiliser du code hérité en tant que fonctions CLR définies par l'utilisateur ou écrire des fonctions définies par l'utilisateur ayant un impact sur les performances en code natif. L'utilisation d'un assembly UNSAFE est obligatoire. Pour connaître les précautions à prendre lors de l’utilisation des assemblys UNSAFE, consultez [Sécurité d’accès du code de l’intégration du CLR](../clr-integration/security/clr-integration-code-access-security.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des fonctions définies par l’utilisateur &#40;moteur de base de données&#41;](create-user-defined-functions-database-engine.md)   
 [Créer des agrégats définis par l'utilisateur](create-user-defined-aggregates.md)   
 [Exécuter les fonctions définies par l'utilisateur](execute-user-defined-functions.md)   
 [Afficher les fonctions définies par l'utilisateur](view-user-defined-functions.md)   
 [Concepts de programmation pour l’intégration du CLR &#40;Common Language Runtime&#41;](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
