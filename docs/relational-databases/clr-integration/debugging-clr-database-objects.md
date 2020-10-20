---
title: Déboguer des objets de base de données CLR (Common Language Runtime)
description: SQL Server prend en charge le débogage des objets Transact-SQL et CLR dans la base de données intégrant SQL Server débogueur avec Microsoft Visual Studio débogueur.
ms.date: 10/06/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: how-to
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 1be293f98a3b78280b16f80ab7dcfcb656f7e0ec
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196890"
---
# <a name="how-to-debug-clr-database-objects"></a>Comment déboguer des objets de base de données CLR

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
 
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le débogage d'objets [!INCLUDE[tsql](../../includes/tsql-md.md)] et CLR dans la base de données. Les principaux atouts du débogage dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont la facilité d'installation et d'utilisation, et l'intégration du débogueur SQL Server avec le débogueur Microsoft Visual Studio. En outre, le débogage fonctionne sur plusieurs langages. Les utilisateurs peuvent effectuer de façon transparente un pas à pas détaillé dans les objets CLR à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] et vice versa. Le débogueur Transact-SQL dans SQL Server Management Studio ne peut pas être utilisé pour déboguer des objets de base de données managés, mais vous pouvez déboguer les objets en utilisant les débogueurs de Visual Studio. Le débogage d'objets de base de données managés dans Visual Studio prend en charge toutes les fonctionnalités de débogage classiques, par exemple, les instructions "step into" et "step over" dans les routines qui s'exécutent sur le serveur. Les débogueurs peuvent définir des points d'arrêt, inspecter la pile des appels, inspecter les variables et modifier des valeurs de variables en cours de débogage. 

> [!NOTE]
> Visual Studio .NET 2003 ne peut pas être utilisé pour le débogage ou la programmation de l’intégration du CLR. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut le .NET Framework préinstallé et Visual Studio .NET 2003 ne peut pas utiliser les assemblys .NET Framework 2.0.  
  
## <a name="debugging-permissions-and-restrictions"></a>Autorisations et restrictions de débogage

Le débogage est une opération hautement privilégiée, et par conséquent, seuls les membres du rôle serveur fixe **sysadmin** sont autorisés à le faire dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Les restrictions suivantes s'appliquent dans le cadre du débogage :  
  
- Le débogage des routines CLR est restreint à une instance de débogueur à la fois. Cette limitation s'applique parce que l'exécution de la totalité du code CLR est gelée lorsqu'un point d'arrêt est atteint et qu'elle ne reprend que lorsque le débogueur continue à partir du point d'arrêt. Toutefois, vous pouvez continuer à déboguer [!INCLUDE[tsql](../../includes/tsql-md.md)] dans d'autres connexions. Bien que le débogage [!INCLUDE[tsql](../../includes/tsql-md.md)] ne gèle pas d'autres exécutions sur le serveur, il peut provoquer la mise en attente d'autres connexions par le maintien d'un verrou.  
  
- Les connexions existantes ne peuvent pas être déboguées ; seules les nouvelles connexions peuvent l'être, puisque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert des informations sur l'environnement du client et du débogueur pour que la connexion puisse être établie.  
  
En raison des restrictions précitées, nous recommandons que le débogage du code [!INCLUDE[tsql](../../includes/tsql-md.md)] et CLR soit effectué sur un serveur de test et non sur un serveur de production.  
  
## <a name="overview"></a>Vue d’ensemble

Le débogage dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suit un modèle « par connexion ». Un débogueur peut détecter et déboguer des activités uniquement sur la connexion cliente à laquelle il est attaché. Comme les fonctionnalités du débogueur ne sont pas limitées par le type de connexion, il est possible de déboguer à la fois des TDS (Tabular Data Stream) et des connexions HTTP. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'autorise pas le débogage des connexions existantes. Le débogage prend en charge toutes les fonctionnalités de débogage communes dans les routines qui s'exécutent sur le serveur. L'interaction entre un débogueur et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'effectue par le biais d'un modèle COM (Component Object Model) distribué.  
  
Pour plus d’informations et des scénarios sur le débogage des procédures stockées managées, des fonctions, des déclencheurs, des types définis par l’utilisateur et des agrégats, consultez [SQL Server le débogage de base de données d’intégration du CLR](/previous-versions/ms165050(v=vs.100)) dans la documentation de Visual Studio.  
  
Le protocole réseau TCP/IP doit être activé sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d'utiliser Visual Studio pour le développement et le débogage distants. Pour plus d’informations sur l’activation du protocole TCP/IP sur le serveur, consultez [configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md).  
  
## <a name="debugging-steps"></a>Étapes de débogage

Pour déboguer un objet de base de données CLR dans Microsoft Visual Studio, procédez comme suit :

1. Ouvrez Microsoft Visual Studio, puis créez un projet de SQL Server. Vous pouvez utiliser l’instance de base de données locale SQL qui est fournie avec Visual Studio.

2. Créer un nouveau type CLR SQL (C#) :

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**, **nouvel élément...**. 
   1. Dans la **fenêtre Ajouter un nouvel élément** , **Sélectionnez procédure stockée c# CLR SQL**, **fonction SQL CLR C# User-Defined**, **SQL CLR C# User-Defined type**, **déclencheur SQL CLR c#**, **agrégat SQL CLR c#** ou **classe**.
   1. Spécifiez un nom pour le fichier source du nouveau type, puis sélectionnez **Ajouter**.

3. Ajoutez le code du nouveau type à l'éditeur de texte. Pour obtenir un exemple de code pour un exemple de procédure stockée, consultez la section exemple ci-dessous dans cet article.

4. Ajoutez un script qui teste le type : 

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet, puis sélectionnez **Ajouter**, **script.**... 
   1. Dans la fenêtre **Ajouter un nouvel élément** , sélectionnez **script (pas dans la génération)**, puis spécifiez un nom, tel que `Test.sql` . Sélectionnez le bouton **Ajouter**.
   1. Dans **Explorateur de solutions**, double-cliquez sur le `Test.sql` nœud pour ouvrir le fichier source du script de test par défaut.
   1. Ajoutez le script de test (un qui appelle le code à déboguer) dans l’éditeur de texte. Consultez l’exemple de la section suivante pour obtenir un exemple de script.

5. Placez un ou plusieurs points d'arrêt dans le code source. Cliquez avec le bouton droit sur une ligne de code dans l’éditeur de texte de la fonction ou de la routine que vous souhaitez déboguer. Sélectionnez **point d’arrêt**, **Insérer un point d’arrêt**. Le point d'arrêt est ajouté et la ligne de code est affichée en rouge.

6. Dans le menu **Déboguer** , sélectionnez **Démarrer le débogage** pour compiler, déployer et tester le projet. Le script de test dans `Test.sql` est exécuté et l’objet de base de données managé est appelé.

7. Lorsque la flèche jaune (désignant le pointeur d’instruction) apparaît au point d’arrêt, l’exécution du code s’interrompt. Vous pouvez ensuite déboguer votre objet de base de données managé :

   1. Utilisez **pas à pas principal** dans le menu **Déboguer** pour faire passer le pointeur d’instruction à la ligne de code suivante.
   1. Utilisez la fenêtre **variables locales** pour observer l’état des objets actuellement mis en surbrillance par le pointeur d’instruction.
   1. Ajoutez des variables à la fenêtre **Espion** . Vous pouvez observer l’état des variables surveillées dans toute la session de débogage, même si la variable n’est pas à la ligne de code actuellement mise en surbrillance par le pointeur d’instruction. 
   1. Sélectionnez **Continuer** dans le menu **Déboguer** pour avancer le pointeur d’instruction jusqu’au point d’arrêt suivant ou pour terminer l’exécution de la routine s’il n’y a plus de points d’arrêt.
  
## <a name="example-code"></a>Exemple de code

L'exemple suivant retourne la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'appelant.  
  
```csharp
using System.Data.SqlClient;
using Microsoft.SqlServer.Server;

public class StoredProcedures
{
    [Microsoft.SqlServer.Server.SqlProcedure]
    public static void GetVersion()
    {
        using (var connection = new SqlConnection("context connection=true"))
        {
            connection.Open();
            var command = new SqlCommand("select @@version", connection);
            SqlContext.Pipe.ExecuteAndSend(command);
        }
    }
}
```

## <a name="example-test-script"></a>Exemple de script de test

Le script de test suivant montre comment appeler la `GetVersion` procédure stockée définie dans l’exemple précédent.  
  
```sql
EXEC GetVersion  
```  

## <a name="next-steps"></a>Étapes suivantes
  
Pour plus d’informations sur le débogage de code managé à l’aide de Visual Studio, consultez [débogage de code managé](/visualstudio/debugger/debugging-managed-code) dans la documentation de Visual Studio.  

Pour plus d’informations, consultez concepts de programmation de l' [intégration du Common Language Runtime](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
