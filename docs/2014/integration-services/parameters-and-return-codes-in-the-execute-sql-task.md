---
title: Paramètres et codes de retour dans la tâche d’exécution SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- return codes [Integration Services]
- parameters [Integration Services]
- parameterized SQL statements [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: a3ca65e8-65cf-4272-9a81-765a706b8663
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 49ac4661e533b4c4e56a750f208c3ded09f72d27
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056788"
---
# <a name="parameters-and-return-codes-in-the-execute-sql-task"></a>Paramètres et codes de retour dans la tâche d'exécution SQL
  Les instructions SQL et les procédures stockées utilisent fréquemment des paramètres de types `input`, `output` et des codes de retour. Dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], la tâche d'exécution SQL prend en charge les types de paramètres `Input`, `Output` et `ReturnValue`. Vous utilisez le type `Input` pour les paramètres d'entrée, `Output` pour les paramètres de sortie et `ReturnValue` pour les codes de retour.  
  
> [!NOTE]  
>  Vous ne pouvez utiliser des paramètres dans une tâche d'exécution SQL que si le fournisseur de données les prend en charge.  
  
 Les paramètres des commandes SQL, notamment les requêtes et les procédures stockées, sont mappés à des variables définies par l'utilisateur créées dans l'étendue de la tâche d'exécution SQL, un conteneur parent ou dans l'étendue du package. Les variables peuvent être définies au moment de la conception ou être remplies dynamiquement lors de l'exécution. Vous pouvez également mapper des paramètres à des variables système. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md) et [Variables système](system-variables.md).  
  
 Toutefois, l'utilisation de paramètres et de codes de retour dans une tâche d'exécution SQL ne permet pas uniquement de savoir quels types de paramètres sont pris en charge par la tâche et de quelle manière ces paramètres seront mappés. D'autres indications et spécifications d'utilisation permettent d'utiliser avec succès des paramètres et des codes de retour dans la tâche d'exécution SQL. Le reste de cette rubrique traite de ces indications et spécifications d'utilisation.  
  
-   [Utilisation des marqueurs et des noms de paramètres](#Parameter_names_and_markers)  
  
-   [Utilisation de paramètres avec des types de données de date et d’heure](#Date_and_time_data_types)  
  
-   [Utilisation de paramètres dans les clauses WHERE](#WHERE_clauses)  
  
-   [Utilisation de paramètres avec des procédures stockées](#Stored_procedures)  
  
-   [Obtention de valeurs de codes de retour](#Return_codes)  
  
-   [Configuration de paramètres et de codes de retour dans l'éditeur de tâche d'exécution SQL](#Configure_parameters_and_return_codes)  
  
##  <a name="Parameter_names_and_markers"></a>Utilisation des marqueurs et des noms de paramètres  
 Selon le type de connexion que la tâche d'exécution SQL utilise, la syntaxe de la commande SQL utilise différents marqueurs de paramètres. Par exemple, le [!INCLUDE[vstecado](../includes/vstecado-md.md)] type de gestionnaire de connexions requiert que la commande SQL utilise un marqueur de paramètre au format ** \@varParameter**, tandis que OLE DB type de connexion nécessite le marqueur de paramètre point d’interrogation ( ?).  
  
 Les noms que vous pouvez utiliser comme noms de paramètres dans les mappages entre variables et paramètres varient également selon le type de gestionnaire de connexions. Par exemple, le type de gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] utilise un nom défini par l'utilisateur avec le préfixe \@, tandis que le type de gestionnaire de connexions OLE DB impose l'utilisation de la valeur numérique d'un ordinal de base 0 comme nom de paramètre.  
  
 Le tableau suivant indique les conditions requises des commandes SQL pour les types de gestionnaires de connexions que la tâche d'exécution SQL peut utiliser.  
  
|Type de connexion|Marqueur de paramètre|Nom du paramètre|Exemple de commande SQL|  
|---------------------|----------------------|--------------------|-------------------------|  
|ADO|?|Param1, Param2, ...|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|\@\<nom du paramètre>|\@\<nom du paramètre>|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = \@parmContactID|  
|ODBC|?|1, 2, 3, ...|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
|EXCEL et OLE DB|?|0, 1, 2, 3, ...|SELECT FirstName, LastName, Title FROM Person.Contact WHERE ContactID = ?|  
  
### <a name="using-parameters-with-adonet-and-ado-connection-managers"></a>Utilisation de paramètres avec les gestionnaires de connexions ADO.NET et ADO  
 Les gestionnaires de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] et ADO ont des spécifications particulières pour les commandes SQL qui utilisent des paramètres :  
  
-   Les gestionnaires de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] exigent que la commande SQL utilise des noms de paramètres comme marqueurs de paramètres. Cela signifie que des variables peuvent être mappées directement à des paramètres. Par exemple, la variable `@varName` est mappée au paramètre nommé `@parName` et fournit une valeur au paramètre `@parName`.  
  
-   Les gestionnaires de connexions ADO.NET imposent que la commande SQL utilise des points d'interrogation (?) comme marqueurs de paramètres. Toutefois, vous pouvez utiliser les noms définis par l'utilisateur, à l'exception des valeurs entières, comme noms de paramètres.  
  
 Pour fournir des valeurs aux paramètres, les variables sont mappées à des noms de paramètres. Puis, la tâche d'exécution SQL utilise la valeur ordinale du nom de paramètre dans la liste des paramètres pour charger des valeurs de variables dans des paramètres.  
  
### <a name="using-parameters-with-excel-odbc-and-ole-db-connection-managers"></a>Utilisation de paramètres avec les gestionnaires de connexions EXCEL, ODBC et OLE DB  
 Les gestionnaires de connexions EXCEL, ODBC et OLE DB imposent que la commande SQL utilise des points d'interrogation (?) comme marqueurs de paramètres et des valeurs numériques de base 0 et de base 1 comme noms de paramètres. Si la tâche d'exécution SQL utilise le gestionnaire de connexions ODBC, le nom de paramètre qui mappe au premier paramètre dans la requête est nommé 1 ; sinon, le paramètre est nommé 0. Pour les paramètres suivants, la valeur numérique du nom de paramètre indique le paramètre dans la commande SQL à laquelle le nom de paramètre mappe. Par exemple, le paramètre nommé 3 est mappé au troisième paramètre, qui est représenté par le troisième point d'interrogation (?) dans la commande SQL.  
  
 Pour fournir des valeurs aux paramètres, les variables sont mappées à des noms de paramètres et la tâche d'exécution SQL utilise la valeur ordinale du nom du paramètre pour charger des valeurs de variables dans des paramètres.  
  
 Selon le fournisseur que le gestionnaire de connexions utilise, certains types de données OLE DB peuvent ne pas être pris en charge. Par exemple, le pilote Excel ne reconnaît qu'un ensemble limité de types de données. Pour plus d’informations sur le comportement du fournisseur Jet avec le pilote Excel, consultez [Source Excel](data-flow/excel-source.md).  
  
#### <a name="using-parameters-with-ole-db-connection-managers"></a>Utilisation de paramètres avec les gestionnaires de connexions OLE DB  
 Quand la tâche d’exécution SQL utilise le gestionnaire de connexions OLE DB, la propriété BypassPrepare de la tâche est disponible. Vous devez définir cette propriété à `true` si la tâche d'exécution SQL utilise des instructions SQL avec des paramètres.  
  
 Lorsque vous utilisez un gestionnaire de connexions OLE DB, vous ne pouvez pas utiliser de sous-requêtes paramétrables, car la tâche d'exécution SQL ne peut pas dériver d'informations de paramètre par le biais du fournisseur OLE DB. Toutefois, vous pouvez utiliser une expression pour concaténer les valeurs des paramètres dans la chaîne de requête et définir la propriété SqlStatementSource de la tâche.  
  
##  <a name="Date_and_time_data_types"></a>Utilisation de paramètres avec des types de données de date et d’heure  
  
### <a name="using-date-and-time-parameters-with-adonet-and-ado-connection-managers"></a>Utilisation de paramètres de date et d'heure avec les gestionnaires de connexions ADO.NET et ADO  
 Lors de la lecture des données des types [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `time` et `datetimeoffset`, une tâche d'exécution SQL qui utilise un gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] ou ADO a les spécifications supplémentaires suivantes :  
  
-   Pour `time` les données, [!INCLUDE[vstecado](../includes/vstecado-md.md)] un gestionnaire de connexions requiert que ces données soient stockées dans un paramètre dont le `Input` type `Output`de paramètre est ou, et `string`dont le type de données est.  
  
-   Pour les données `datetimeoffset`, un gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] impose que ces données soient stockées dans l'un des paramètres suivants :  
  
    -   Un paramètre de type `Input` et dont le type de données est `string`.  
  
    -   Un paramètre de type `Output` ou `ReturnValue` et dont le type de données est `datetimeoffset`, `string` ou `datetime2`. Si vous sélectionnez un paramètre dont le type de données est `string` ou `datetime2`, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] convertit les données en string ou datetime2.  
  
-   Un gestionnaire de connexions ADO impose que les données `time` ou `datetimeoffset` soient stockées dans un paramètre de type `Input` ou `Output` et dont le type de données est `adVarWchar`.  
  
 Pour plus d’informations sur les types de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et leur mappage aux types de données [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) et [Types de données d’Integration Services](data-flow/integration-services-data-types.md).  
  
### <a name="using-date-and-time-parameters-with-ole-db-connection-managers"></a>Utilisation de paramètres de date et d'heure avec les gestionnaires de connexions OLE DB  
 Lors de l'utilisation d'un gestionnaire de connexions OLE DB, une tâche d'exécution SQL a des spécifications de stockage particulières pour les données des types [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `date`, `time`, `datetime`, `datetime2` et `datetimeoffset`. Vous devez stocker ces données dans l'un des types de paramètres suivants :  
  
-   Un paramètre d'entrée doté du type de données NVARCHAR.  
  
-   Un paramètre de sortie doté du type de données approprié, tel que répertorié dans le tableau suivant.  
  
    |`Output`type de paramètre|Type de données Date|  
    |-------------------------------|--------------------|  
    |DBDATE|`date`|  
    |DBTIME2|`time`|  
    |DBTIMESTAMP|`datetime`, `datetime2`|  
    |DBTIMESTAMPOFFSET|`datetimeoffset`|  
  
 Si les données ne sont pas stockées dans le paramètre d'entrée ou de sortie approprié, le package échoue.  
  
### <a name="using-date-and-time-parameters-with-odbc-connection-managers"></a>Utilisation de paramètres de date et d'heure avec les gestionnaires de connexions ODBC  
 Lors de l'utilisation d'un gestionnaire de connexions ODBC, une tâche d'exécution SQL a des spécifications de stockage particulières pour les données de l'un des types [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `date`, `time`, `datetime`, `datetime2` ou `datetimeoffset`. Vous devez stocker ces données dans l'un des types de paramètres suivants :  
  
-   Un paramètre de type `input` doté du type de données SQL_WVARCHAR  
  
-   Un paramètre de type `output` doté du type de données approprié, tel que répertorié dans le tableau suivant.  
  
    |`Output`type de paramètre|Type de données Date|  
    |-------------------------------|--------------------|  
    |SQL_DATE|`date`|  
    |SQL_SS_TIME2|`time`|  
    |SQL_TYPE_TIMESTAMP<br /><br /> -ou-<br /><br /> SQL_TIMESTAMP|`datetime`, `datetime2`|  
    |SQL_SS_TIMESTAMPOFFSET|`datetimeoffset`|  
  
 Si les données ne sont pas stockées dans le paramètre d'entrée ou de sortie approprié, le package échoue.  
  
##  <a name="WHERE_clauses"></a>Utilisation de paramètres dans les clauses WHERE  
 Les commandes SELECT, INSERT, UPDATE et DELETE incluent fréquemment des clauses WHERE pour spécifier des filtres qui définissent les conditions auxquelles chaque ligne des tables sources doit satisfaire pour se qualifier pour une commande SQL. Les paramètres fournissent les valeurs de filtre dans les clauses WHERE.  
  
 Vous pouvez utiliser des marqueurs de paramètres pour fournir dynamiquement des valeurs de paramètres. Les règles pour lesquelles des marqueurs de paramètres et des noms de paramètres peuvent être utilisés dans l'instruction SQL varient selon le type de gestionnaire de connexions que la tâche d'exécution SQL utilise.  
  
 Le tableau suivant présente des exemples de la commande SELECT par type de gestionnaire de connexions. Les instructions INSERT, UPDATE et DELETE sont similaires. Les exemples utilisent la commande SELECT pour retourner les produits de la table **Product** dans [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] qui ont un **ProductID** supérieur et inférieur aux valeurs spécifiées par deux paramètres.  
  
|Type de connexion|Syntaxe SELECT|  
|---------------------|-------------------|  
|EXCEL, ODBC et OLEDB|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
|ADO|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
 Les exemples requièrent des paramètres avec les noms suivants :  
  
-   Les gestionnaires de connexions EXCEL et OLED DB utilisent les noms de paramètres 0 et 1. Le type de connexion ODBC utilise 1 et 2.  
  
-   Le type de connexion ADO peut utiliser deux noms de paramètres (par exemple, Param1 et Param2), mais les paramètres doivent être mappés selon leur position ordinale dans la liste des paramètres.  
  
-   Le type de connexion [!INCLUDE[vstecado](../includes/vstecado-md.md)] utilise les noms de paramètres \@parmMinProductID et \@parmMaxProductID.  
  
##  <a name="Stored_procedures"></a>Utilisation de paramètres avec des procédures stockées  
 Les commandes SQL qui exécutent des procédures stockées peuvent également utiliser le mappage de paramètres. Les règles d'utilisation des marqueurs de paramètres et des noms de paramètres varient selon le type de gestionnaire de connexions que la tâche d'exécution SQL utilise, tout comme les règles des requêtes paramétrables.  
  
 Le tableau suivant présente des exemples de la commande EXEC par type de gestionnaire de connexions. Les exemples exécutent la procédure stockée **uspGetBillOfMaterials** dans [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]. La procédure stockée utilise `@StartProductID` les `@CheckDate` `input` paramètres et.  
  
|Type de connexion|Syntaxe EXEC|  
|---------------------|-----------------|  
|EXCEL et OLEDB|`EXEC uspGetBillOfMaterials ?, ?`|  
|ODBC|`{call uspGetBillOfMaterials(?, ?)}`<br /><br /> Pour plus d’informations sur la syntaxe d’appel ODBC, consultez la rubrique [Paramètres de procédure](https://go.microsoft.com/fwlink/?LinkId=89462) dans le Guide de référence du programmeur ODBC publié dans MSDN Library.|  
|ADO|Si IsQueryStoredProcedure a la valeur `False`,`EXEC uspGetBillOfMaterials ?, ?`<br /><br /> Si IsQueryStoredProcedure a la valeur `True`,`uspGetBillOfMaterials`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Si IsQueryStoredProcedure a la valeur `False`,`EXEC uspGetBillOfMaterials @StartProductID, @CheckDate`<br /><br /> Si IsQueryStoredProcedure a la valeur `True`,`uspGetBillOfMaterials`|  
  
 Pour utiliser des paramètres de sortie, la syntaxe impose que le mot clé OUTPUT suive chaque marqueur de paramètre. Par exemple, la syntaxe de paramètre de sortie suivante est correcte : `EXEC myStoredProcedure ? OUTPUT`.  
  
 Pour plus d’informations sur l’utilisation de paramètres d’entrée et de sortie avec des procédures stockées Transact-SQL, consultez [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).  
  
##  <a name="Return_codes"></a>Obtention de valeurs de codes de retour  
 Une procédure stockée peut retourner une valeur entière appelée « code de retour » pour indiquer l'état d'exécution d'une procédure. Pour implémenter des codes de retour dans la tâche d'exécution SQL, vous utilisez des paramètres du type `ReturnValue`.  
  
 Le tableau suivant présente par type de connexion des exemples de commandes EXEC qui implémentent des codes de retour. Tous les exemples utilisent un paramètre de type `input`. Les règles d’utilisation des marqueurs de paramètres et des noms de paramètres sont les mêmes pour tous`Input`les `Output`types de `ReturnValue`paramètres :, et.  
  
 Certaines syntaxes ne prennent pas en charge les littéraux de paramètres. Dans ce cas, vous devez fournir la valeur du paramètre en utilisant une variable.  
  
|Type de connexion|Syntaxe EXEC|  
|---------------------|-----------------|  
|EXCEL et OLEDB|`EXEC ? = myStoredProcedure 1`|  
|ODBC|`{? = call myStoredProcedure(1)}`<br /><br /> Pour plus d’informations sur la syntaxe d’appel ODBC, consultez la rubrique [Paramètres de procédure](https://go.microsoft.com/fwlink/?LinkId=89462) dans le Guide de référence du programmeur ODBC publié dans MSDN Library.|  
|ADO|Si IsQueryStoreProcedure a la valeur `False`,`EXEC ? = myStoredProcedure 1`<br /><br /> Si IsQueryStoreProcedure a la valeur `True`,`myStoredProcedure`|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Set IsQueryStoreProcedure a la valeur `True`.<br /><br /> `myStoredProcedure`|  
  
 Dans la syntaxe affichée dans la table précédente, la tâche d’exécution SQL utilise le type de source **Entrée directe** pour exécuter la procédure stockée. La tâche d’exécution SQL peut aussi utiliser le type de source **Connexion de fichiers** pour exécuter une procédure stockée. Que la tâche d’exécution SQL utilise ou non le type de source de **connexion de fichiers** ou **d’entrée directe** , `ReturnValue` utilisez un paramètre du type pour implémenter le code de retour. Pour plus d’informations sur la configuration du type de source de l’instruction SQL exécutée par la tâche d’exécution SQL, consultez [Éditeur de tâche d’exécution de requêtes SQL &#40;page Général&#41;](general-page-of-integration-services-designers-options.md).  
  
 Pour plus d’informations sur l’utilisation de codes de retour avec des procédures stockées Transact-SQL, consultez [RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql).  
  
##  <a name="Configure_parameters_and_return_codes"></a>Configuration des paramètres et des codes de retour dans la tâche d’exécution SQL  
 Pour plus d’informations sur les propriétés de paramètres et de codes de retour que vous pouvez définir dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Éditeur de tâche d’exécution de SQL &#40;page mappage de paramètre&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 [Définir les propriétés d'une tâche ou d'un conteneur](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Entrée de blog, [Procédures stockées avec paramètres de sortie](https://go.microsoft.com/fwlink/?LinkId=157786), sur blogs.msdn.com  
  
-   Exemple CodePlex, [Execute SQL Parameters and Result Sets](https://go.microsoft.com/fwlink/?LinkId=157863)(en anglais), sur msftisprodsamples.codeplex.com  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes SQL, tâche](control-flow/execute-sql-task.md)   
 [Ensembles de résultats dans la tâche d’exécution SQL](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
  
