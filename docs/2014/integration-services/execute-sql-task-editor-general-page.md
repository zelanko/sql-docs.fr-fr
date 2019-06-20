---
title: Exécuter l’éditeur de tâche SQL (Page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.general.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: beb39086-28ce-46af-b6d8-f7b4fb8d9069
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 96d211defa789888a3fd7b513b4dff60fa795cb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66058988"
---
# <a name="execute-sql-task-editor-general-page"></a>Éditeur de tâche d'exécution SQL (page Général)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur de tâche d'exécution SQL** pour configurer la tâche d'exécution SQL et indiquer l'instruction SQL que la tâche exécuter.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche d’exécution de requêtes SQL](control-flow/execute-sql-task.md), [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) et [Ensembles de résultats dans la tâche d’exécution SQL](../../2014/integration-services/result-sets-in-the-execute-sql-task.md). Pour plus d’informations sur le langage Transact-SQL, consultez [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference).  
  
## <a name="static-options"></a>Options statiques  
 **Nom**  
 Donnez un nom unique à la tâche d'exécution SQL dans le flux de travail. Le nom fourni est affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrit la tâche d'exécution SQL. Pour réaliser des packages autodocumentés plus faciles à maintenir, fournissez une description de la tâche en rapport avec son objectif.  
  
 **TimeOut**  
 Spécifiez le nombre maximal de secondes d'exécution de la tâche au terme duquel le délai d'attente expire. La valeur 0 indique un délai infini. La valeur par défaut est 0.  
  
> [!NOTE]  
>  Les procédures stockées ne sont par concernées par le délai d'expiration si elles émulent la fonctionnalité de veille en laissant le temps nécessaire à l'établissement des connexions et à la réalisation des transactions qui est supérieur au nombre de secondes spécifié par l'option **TimeOut**. Cependant, les procédures stockées qui exécutent des requêtes sont toujours soumises à la limitation de temps spécifiée dans **TimeOut**.  
  
 **CodePage**  
 Spécifiez la page de codes à utiliser pour la traduction des valeurs Unicode en variables. Il s'agit par défaut de la page de codes de l'ordinateur local.  
  
> [!NOTE]  
>  Lorsque la tâche d'exécution SQL utilise un gestionnaire de connexions ADO ou ODBC, la propriété **CodePage** n'est pas disponible. Si votre solution requiert l'utilisation d'une page de codes, utilisez un gestionnaire de connexions OLE DB ou ADO.NET avec la tâche d'exécution SQL.  
  
 **TypeConversionMode**  
 Lorsque vous définissez cette propriété sur `Allowed`, la tâche d'exécution SQL tente de convertir le paramètre de sortie et les résultats de la requête dans le type de données de la variable à laquelle les résultats sont affectés. Cela s'applique au type de jeu de résultats **Ligne unique** .  
  
 **ResultSet**  
 Spécifiez le type de résultats attendu par l'instruction SQL en cours d'exécution. Choisissez parmi les options suivantes : **Ligne unique**, **Ensemble de résultats complet**, **XML**ou **Aucun**.  
  
 **ConnectionType**  
 Choisissez le type de gestionnaire de connexions à utiliser pour vous connecter à la source de données. Les types de connexions disponibles sont **OLE DB**, **ODBC**, **ADO**, **ADO.NET** et **SQLMOBILE**.  
  
 **Rubriques connexes :** [Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md), [Gestionnaire de connexions ODBC](connection-manager/odbc-connection-manager.md), [Gestionnaire de connexions ADO](connection-manager/ado-connection-manager.md), [Gestionnaire de connexions ADO.NET](connection-manager/ado-net-connection-manager.md), [Gestionnaire de connexions de SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md)  
  
 **Connexion**  
 Choisissez la connexion dans la liste des gestionnaires de connexions définis. Pour créer une connexion, sélectionnez \<**Nouvelle connexion...**>.  
  
 **SQLSourceType**  
 Sélectionnez le type de source de l'instruction SQL qui exécute la tâche.  
  
 Selon le type de gestionnaire de connexions que la tâche d'exécution SQL utilise, vous devez utiliser des marqueurs de paramètres spécifiques dans les instructions SQL paramétrables.  
  
 **Rubriques connexes :** Section des commandes SQL paramétrables en cours d’exécution [tâche d’exécution SQL](control-flow/execute-sql-task.md)  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Entrée directe**|Définissez la source d'une instruction Transact-SQL. Sélectionnez cette valeur pour afficher l'option dynamique **SQLStatement**.|  
|**Connexion de fichiers**|Sélectionnez un fichier qui contient une instruction Transact-SQL. Configurez cette option pour afficher l'option dynamique **FileConnection**.|  
|**Variable**|Définissez la source sur une variable qui définit l'instruction Transact-SQL. Sélectionnez cette valeur pour afficher l'option dynamique **SourceVariable**.|  
  
 **QueryIsStoredProcedure**  
 Indique si l'instruction SQL spécifiée à exécuter est une procédure stockée. Cette propriété est en lecture/écriture uniquement si la tâche utilise le gestionnaire de connexions ADO. Sinon, elle est en lecture seule ; sa valeur est alors `false`.  
  
 **BypassPrepare**  
 Indiquez si l'instruction SQL est préparée.  `true` ignore la préparation ; `false` prépare l'instruction SQL avant de l'exécuter. Cette option est disponible uniquement avec les connexions OLE DB qui prennent en charge la préparation.  
  
 **Rubriques connexes :**  [Exécution préparée](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
 **Parcourir**  
 Utilisez la boîte de dialogue **Ouvrir** pour rechercher un fichier qui contient une instruction SQL. Sélectionnez un fichier dont vous voulez copier le contenu en tant qu'instruction SQL dans la propriété **SQLStatement** .  
  
 **Générer la requête**  
 Créez une instruction SQL au moyen de la boîte de dialogue **Générateur de requêtes** : il s’agit d’un outil graphique de création de requêtes. Cette option est disponible lorsque l'option **SQLSourceType** est configurée avec **Entrée directe**.  
  
 **Analyser la requête**  
 Valide la syntaxe de l’instruction SQL.  
  
## <a name="sqlsourcetype-dynamic-options"></a>Options dynamiques SQLSourceType  
  
### <a name="sqlsourcetype--direct-input"></a>SQLSourceType = Entrée directe  
 **SQLStatement**  
 Dans la zone des options, tapez l’instruction SQL à exécuter ou cliquez sur le bouton d’exploration (...) pour taper l’instruction SQL dans la boîte de dialogue **Entrer une requête SQL**. Vous pouvez également cliquer sur **Générer la requête** pour composer l’instruction à l’aide de la boîte de dialogue **Générateur de requêtes**.  
  
 **Rubriques connexes :** [Générateur de requêtes](../../2014/integration-services/query-builder.md)  
  
### <a name="sqlsourcetype--file-connection"></a>SQLSourceType = Connexion de fichiers  
 **FileConnection**  
 Sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="sqlsourcetype--variable"></a>SQLSourceType = Variable  
 **SourceVariable**  
 Sélectionnez une variable existante ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche SQL exécution &#40;Page mappage de paramètre&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)   
 [Éditeur de tâche SQL exécution &#40;Page ensemble de résultats&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)  
  
  
