---
title: Créer une procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- new stored procedures
- stored procedures [SQL Server], creating
- creating stored procedures
ms.assetid: 76e8a6ba-1381-4620-b356-4311e1331ca7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9aa5518ee9ebcaca287b76636d6eeea8af2f4ea5
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72796421"
---
# <a name="create-a-stored-procedure"></a>Créer une procédure stockée
  Cette rubrique explique comment créer une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE PROCEDURE.  
  
##  <a name="Top"></a>   
-   **Avant de commencer :**  [Autorisations](#Permissions)  
  
-   **Pour créer une procédure, utilisez :**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="Permissions"></a> Permissions  
 Nécessite l'autorisation CREATE PROCEDURE dans la base de données et l'autorisation ALTER sur le schéma dans lequel la procédure est créée.  
  
##  <a name="Procedures"></a> Comment créer une procédure stockée  
 Vous pouvez utiliser l'un des éléments suivants :  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour créer une procédure dans l'Explorateur d'objets**  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , puis **Programmabilité**.  
  
3.  Cliquez avec le bouton droit sur **Procédures stockées**, puis cliquez sur **Nouvelle procédure stockée**.  
  
4.  Dans le menu **Requête** , cliquez sur **Spécifier les valeurs des paramètres du modèle**.  
  
5.  Dans la boîte de dialogue **Spécifier les valeurs des paramètres du modèle** , entrez les valeurs suivantes pour les paramètres affichés.  
  
    |Paramètre|Value|  
    |---------------|-----------|  
    |Author|*Votre nom*|  
    |Date de création|*Date du jour*|  
    |Description|Retourne des données sur les employés.|  
    |Procedure_name|HumanResources.uspGetEmployeesTest|  
    |@Param1|@LastName|  
    |@Datatype_For_Param1|`nvarchar`(50)|  
    |Default_Value_For_Param1|NULL|  
    |@Param2|@FirstName|  
    |@Datatype_For_Param2|`nvarchar`(50)|  
    |Default_Value_For_Param2|NULL|  
  
6.  Cliquez sur **OK**.  
  
7.  Dans l' **Éditeur de requête**, remplacez l'instruction SELECT par l'instruction suivante :  
  
    ```sql  
    SELECT FirstName, LastName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory  
    WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    ```  
  
8.  Pour tester la syntaxe, dans le menu **Requête** , cliquez sur **Analyser**. Si un message d'erreur est retourné, comparez les instructions avec les informations ci-dessus et apportez les corrections nécessaires.  
  
9. Pour créer la procédure, dans le menu **Requête** , cliquez sur **Exécuter**. La procédure est créée en tant qu'objet dans la base de données.  
  
10. Pour afficher la procédure répertoriée dans l’Explorateur d’objets, cliquez avec le bouton droit sur **Procédures stockées** et sélectionnez **Actualiser**.  
  
11. Pour exécuter la procédure, dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nom de la procédure stockée **HumanResources.uspGetEmployeesTest** et sélectionnez **Exécuter la procédure stockée**.  
  
12. Dans la fenêtre **Exécuter la procédure** , entrez Margheim comme valeur pour le paramètre @LastName et entrez la valeur Diane comme valeur pour le paramètre @FirstName.  
  
> [!WARNING]  
>  Validez toutes les entrées utilisateur. Ne concaténez pas les entrées utilisateur avant de les avoir validées. N'exécutez jamais une commande élaborée à partir d'une entrée utilisateur non validée.  
  
###  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour créer une procédure dans l'Éditeur de requête**  
  
1.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans le menu **Fichier** , cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple crée la même procédure stockée que ci-dessus à l'aide d'un nom de procédure différent.  
  
    ```sql
    USE AdventureWorks2012;  
    GO  
    CREATE PROCEDURE HumanResources.uspGetEmployeesTest2   
        @LastName nvarchar(50),   
        @FirstName nvarchar(50)   
    AS
  
        SET NOCOUNT ON;  
        SELECT FirstName, LastName, Department  
        FROM HumanResources.vEmployeeDepartmentHistory  
        WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    GO
    ```  
  
4.  Pour exécuter la procédure, copiez et collez l'exemple suivant dans une nouvelle fenêtre de requête, puis cliquez sur **Exécuter**. Notez que différentes méthodes de spécification des valeurs de paramètre sont affichées.  
  
    ```sql
    EXECUTE HumanResources.uspGetEmployeesTest2 N'Ackerman', N'Pilar';  
    -- Or  
    EXEC HumanResources.uspGetEmployeesTest2 @LastName = N'Ackerman', @FirstName = N'Pilar';  
    GO  
    -- Or  
    EXECUTE HumanResources.uspGetEmployeesTest2 @FirstName = N'Pilar', @LastName = N'Ackerman';  
    GO
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)  
  