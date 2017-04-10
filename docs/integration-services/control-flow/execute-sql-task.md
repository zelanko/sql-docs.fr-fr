---
title: "Tache d&#39;ex&#233;cution de requ&#234;tes SQL | Microsoft Docs"
ms.custom: 
  - "ssisdev020617"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.executesqltask.f1"
  - "sql13.dts.designer.executesqltask.general.f1"
  - "sql13.dts.designer.executesqltask.parametermapping.f1"
  - "sql13.dts.designer.executesqltask.resultset.f1"
helpviewer_keywords: 
  - "instructions Transact-SQL, SSIS"
  - "instructions [Integration Services]"
  - "traitements [Integration Services]"
  - "tâche d'exécution de requêtes SQL [Integration Services]"
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
caps.latest.revision: 115
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 113
---
# Tache d&#39;ex&#233;cution de requ&#234;tes SQL
  La tâche d'exécution SQL exécute des instructions ou des procédures stockées SQL à partir d'un package. La tâche peut contenir une seule ou plusieurs instructions SQL s'exécutant de façon séquentielle. Vous pouvez utiliser la tâche d'exécution SQL aux fins suivantes :  
  
-   Tronquer une table ou une vue pour la préparer à l'insertion de données.  
  
-   Créer, modifier et supprimer des objets de base de données tels que des tables et des vues.  
  
-   Recréer des tables de faits et de dimension avant d'y charger des données.  
  
-   Exécuter des procédures stockées. Si l'instruction SQL appelle une procédure stockée qui retourne des résultats à partir d'une table temporaire, utilisez l'option WITH RESULT SETS afin de définir les métadonnées du jeu de résultats.  
  
-   Enregistrer dans une variable l'ensemble de lignes retourné par une requête.  
  
 Vous pouvez combiner la tâche d'exécution SQL et les conteneurs de boucles Foreach et For pour exécuter plusieurs instructions SQL. Ces conteneurs mettent en œuvre des flux de contrôle répétitifs dans un package et peuvent exécuter la tâche d'exécution SQL de façon répétée. Par exemple, à l'aide du conteneur de boucles Foreach, un package peut passer en revue les fichiers d'un dossier et exécuter une tâche d'exécution SQL de façon répétée afin d'exécuter l'instruction SQL stockée dans chaque fichier.  
  
## Connexion à une source de données  
 La tâche d'exécution SQL peut utiliser différents types de gestionnaires de connexions pour se connecter à la source de données dans laquelle elle exécute l'instruction ou la procédure stockée SQL. La tâche peut utiliser les types de connexion décrits dans le tableau suivant.  
  
|Type de connexion|Gestionnaire de connexions|  
|---------------------|------------------------|  
|EXCEL|[Gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager.md)|  
|OLE DB|[Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|  
|ODBC|[Gestionnaire de connexions ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|  
|ADO|[Gestionnaire de connexions ADO](../../integration-services/connection-manager/ado-connection-manager.md)|  
|ADO.NET|[Gestionnaire de connexions ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|  
|SQLMOBILE|[Gestionnaire de connexions de SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## Création d'instructions SQL  
 La source des instructions SQL utilisée par cette tâche peut être une propriété de tâche contenant une instruction, une connexion à un fichier contenant une ou plusieurs instructions ou le nom d'une variable contenant une instruction. Les instructions SQL doivent être écrites dans le langage du système de gestion de bases de données (SGBD) source. Pour plus d’informations, consultez [Requêtes Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-queries.md).  
  
 Si les instructions SQL sont stockées dans un fichier, la tâche utilise un gestionnaire de connexions de fichiers pour se connecter au fichier. Pour plus d’informations, consultez [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
 Dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], vous pouvez utiliser la boîte de dialogue **Éditeur de tâche d’exécution de requêtes SQL** pour taper des instructions SQL ou utiliser le **Générateur de requêtes**, une interface graphique utilisateur permettant de créer des requêtes SQL. Pour plus d’informations, consultez [Éditeur de tâche d’exécution de requêtes SQL &#40;page Général&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md) et [Générateur de requêtes](../Topic/Query%20Builder.md).  
  
> [!NOTE]  
>  Les instructions SQL valides écrites en dehors de la tâche d'exécution SQL peuvent ne pas être analysées correctement par celle-ci.  
  
> [!NOTE]  
>  La tâche d’exécution de requêtes SQL utilise la valeur d’énumération **RecognizeAll** ParseMode. Pour plus d’informations, consultez [ManagedBatchParser Namespace](http://go.microsoft.com/fwlink/?LinkId=223617) (Espace de noms ManagedBatchParser).  
  
## Envoi de plusieurs instructions dans un traitement  
 Si vous incluez plusieurs instructions dans une tâche d'exécution SQL, vous pouvez les regrouper et les exécuter sous forme de traitement. Pour indiquer la fin d'un traitement, utilisez la commande GO. Toutes les instructions SQL comprises entre deux commandes GO sont envoyées dans un traitement au fournisseur OLE DB afin d'être exécutées. La commande SQL peut comprendre plusieurs traitements séparés par des commandes GO.  
  
 Il existe des restrictions sur les types d'instructions SQL pouvant être regroupées dans un traitement. Pour plus d’informations, consultez [Lots d’instructions](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).  
  
 Si la tâche d'exécution SQL exécute un traitement d'instructions SQL, les règles suivantes s'appliquent à celui-ci :  
  
-   Une seule instruction peut retourner un ensemble de résultats et il doit s'agir de la première instruction du traitement.  
  
-   Si l'ensemble de résultats utilise des liaisons de résultats, les requêtes doivent retourner le même nombre de colonnes. Si les requêtes retournent un nombre différent de colonnes, la tâche échoue. Toutefois, même si la tâche échoue, les requêtes qu'elle exécute, telles que les requêtes DELETE ou INSERT, peuvent réussir.  
  
-   Si les liaisons de résultats utilisent des noms de colonne, la requête doit retourner des colonnes portant les mêmes noms que l'ensemble de résultats utilisé par la tâche. Si les colonnes sont manquantes, la tâche échoue.  
  
-   Si la tâche utilise la liaison de paramètre, toutes les requêtes du traitement doivent avoir le même nombre et les mêmes types de paramètres.  
  
## Exécution de commandes SQL paramétrables  
 Les instructions et les procédures stockées SQL utilisent fréquemment des paramètres d'entrée, des paramètres de sortie et des codes de retour. La tâche d’exécution de requêtes SQL prend en charge les types de paramètres **Input**, **Output** et **ReturnValue**. Vous utilisez le type **Input** pour les paramètres d’entrée, **Output** pour les paramètres de sortie et **ReturnValue** pour les codes de retour.  
  
> [!NOTE]  
>  Vous ne pouvez utiliser des paramètres dans une tâche d'exécution SQL que si le fournisseur de données les prend en charge.  
  
 Pour plus d’informations sur l’utilisation de paramètres et de codes de retour dans la tâche d’exécution de requêtes SQL, consultez [Paramètres et codes de retour dans la tâche d’exécution SQL](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md).  
  
## Spécification d'un type d'ensemble de résultats  
 Selon le type de commande SQL, un ensemble de résultats peut ou non être retourné à la tâche d'exécution SQL. Par exemple, une instruction SELECT retourne généralement un ensemble de résultats, contrairement à une instruction INSERT. L'ensemble de résultats issu d'une instruction SELECT peut contenir un nombre de lignes quelconque (aucune ligne, une ligne ou de nombreuses lignes). Les procédures stockées peuvent également retourner une valeur entière, appelée « code de retour », qui indique l'état de leur exécution. Dans ce cas, l'ensemble de résultats comprend une seule ligne.  
  
 Pour plus d’informations sur la récupération de jeux de résultats à partir de commandes SQL dans la tâche d’exécution SQL, consultez [Ensembles de résultats dans la tâche d’exécution SQL](../Topic/Result%20Sets%20in%20the%20Execute%20SQL%20Task.md).  
  
## Résolution des problèmes liés à la tâche d'exécution SQL  
 Vous pouvez consigner les appels que la tâche d'exécution SQL effectue auprès de fournisseurs de données externes. Vous pouvez utiliser cette fonctionnalité de journalisation pour résoudre les problèmes liés aux commandes SQL qu'exécute la tâche d'exécution SQL. Pour consigner les appels que la tâche d’exécution SQL passe à des fournisseurs de données externes, activez la journalisation des packages et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Parfois, une commande SQL ou une procédure stockée retourne plusieurs jeux de résultats. Ces jeux de résultats incluent non seulement des ensembles de lignes qui sont le résultat de requêtes **SELECT**, mais également des valeurs uniques qui sont le résultat d’erreurs d’instructions **RAISERROR** ou **PRINT**. Le fait que la tâche ignore les erreurs dans des jeux de résultats qui se produisent après le premier jeu de résultats dépend du type de gestionnaire de connexions utilisé :  
  
-   Lorsque vous utilisez les gestionnaires de connexions OLE DB et ADO, la tâche ignore les jeux de résultats qui se produisent après le premier jeu de résultats. Par conséquent, avec ces gestionnaires de connexions, la tâche ignore une erreur retournée par une commande SQL ou une procédure stockée lorsque l'erreur ne fait pas partie du premier jeu de résultats.  
  
-   Lorsque vous utilisez les gestionnaires de connexions ODBC et ADO.NET, la tâche n'ignore pas les jeux de résultats qui se produisent après le premier jeu de résultats. Avec ces gestionnaires de connexions, la tâche échoue avec une erreur quand un jeu de résultats autre que le premier jeu de résultats contient une erreur.  
  
### Entrées de journal personnalisées  
 Le tableau suivant décrit les entrées de journal personnalisées pour la tâche d'exécution SQL. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|**ExecuteSQLExecutingQuery**|Fournit des informations sur les phases d'exécution de l'instruction SQL. Des entrées de journal sont écrites lorsque la tâche acquiert la connexion à la base de données, lorsqu'elle commence à préparer l'instruction SQL et à la fin de l'exécution de l'instruction SQL. L'entrée de journal concernant la phase de préparation inclut l'instruction SQL que la tâche utilise.|  
  
## Configuration de la tâche d'exécution SQL  
 Vous pouvez configurer la tâche d'exécution SQL comme suit :  
  
-   Spécifiez le type de gestionnaire de connexions à utiliser pour établir la connexion à une base de données.  
  
-   Spécifiez le type d'ensemble de résultats retourné par l'instruction SQL.  
  
-   Spécifiez un délai d'expiration pour les instructions SQL.  
  
-   Spécifiez la source de l'instruction SQL.  
  
-   Indiquez si la tâche passe la phase de préparation de l'instruction SQL.  
  
-   Si vous utilisez le type de connexion ADO, indiquez si l'instruction SQL est une procédure stockée. Pour d’autres types de connexion, cette propriété est définie en lecture seule et sa valeur est toujours **false**.  
  
 Vous pouvez définir les propriétés par programmation ou par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche d’exécution de requêtes SQL &#40;page Général&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Éditeur de tâche d’exécution de requêtes SQL &#40;page Mappage de paramètre&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Parameter%20Mapping%20Page\).md)  
  
-   [Éditeur de tâche d’exécution de requêtes SQL &#40;page Ensemble de résultats&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Result%20Set%20Page\).md)  
  
-   [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Configuration de la tâche d'exécution SQL par programmation  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## Tâches associées  
  
-   [Mapper des paramètres de requête à des variables dans une tâche d'exécution SQL](../Topic/Map%20Query%20Parameters%20to%20Variables%20in%20an%20Execute%20SQL%20Task.md)  
  
-   [Mapper des ensembles de résultats à des variables dans une tâche d'exécution SQL](../Topic/Map%20Result%20Sets%20to%20Variables%20in%20an%20Execute%20SQL%20Task.md)  
  
## Contenu connexe  
  
-   [Paramètres et codes de retour dans la tâche d'exécution SQL](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md)  
  
-   [Ensembles de résultats dans la tâche d'exécution SQL](../Topic/Result%20Sets%20in%20the%20Execute%20SQL%20Task.md)  
  
-   [Référence Transact-SQL &#40;moteur de base de données&#41;](../../t-sql/transact-sql-reference-database-engine.md)  
  
-   Entrée de blog, [New Date and Time Functions in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=239783), sur le site mssqltips.com  
  
  