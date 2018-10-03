---
title: Constantes énumérées dans des expressions de propriété | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bb882f13b7f4fd19cab5f9b44885647aaafa65d3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089658"
---
# <a name="enumerated-constants-in-property-expressions"></a>Constantes énumérées dans des expressions de propriété
  Si des expressions de propriété incluent des valeurs d'une liste de membres d'énumérateur, l'expression doit utiliser la valeur numérique du membre énumérateur et non le nom convivial du membre. Par exemple, si une expression définit la `LoggingMode` propriété, vous devez utiliser la valeur numérique 2 au lieu du nom convivial désactivé.  
  
 Cette rubrique répertorie uniquement les valeurs numériques équivalant aux noms conviviaux d'énumérateurs dont les membres sont fréquemment utilisés dans des expressions de propriété. Le modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut de nombreux énumérateurs supplémentaires que vous utilisez quand vous programmez le modèle objet pour générer des packages par programmation ou des éléments de package de code personnalisé, tels que des tâches et des composants de flux de données.  
  
 En complément des propriétés personnalisées pour les packages et les objets package, la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] inclut un jeu de propriétés accessibles aux packages, aux tâches, ainsi qu'aux conteneurs de boucles Foreach, de boucles For et de séquences. Les propriétés communes qui sont définies par des valeurs provenant d'énumérateurs (`ForceExecutionResult`, `LoggingMode`, `IsolationLevel` et `Transaction Option`) sont répertoriées dans la section Propriétés communes.  
  
 Les sections suivantes fournissent des informations sur les constantes énumérées :  
  
 [Package](#Package)  
  
 [Énumérateurs de boucles Foreach](#Foreach)  
  
 [Tâches](#Tasks)  
  
 [Tâches du plan de maintenance](#MaintenancePlanTasks)  
  
 [Propriétés communes](#CommonProperties)  
  
##  <a name="Package"></a> Package  
 Les tableaux suivants répertorient les noms conviviaux et les équivalents en valeur numérique pour des propriétés de packages que vous définissez à l'aide de valeurs provenant d'un énumérateur.  
  
 `PackageType` propriété, définie à l’aide de valeurs à partir de la `DTSPackageType` énumération.  
  
|Nom convivial dans DTSPackageType|Valeur numérique|  
|-------------------------------------|-------------------|  
|Par défaut|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage` propriété, définie à l’aide de valeurs à partir de la `DTSCheckpointUsage` énumération.  
  
|Nom convivial dans DTSCheckpointUsage|Valeur numérique|  
|-----------------------------------------|-------------------|  
|Never|0|  
|IfExists|1|  
|Always|2|  
  
 `PackagePriorityClass` propriété, définie à l’aide de valeurs à partir de la `DTSPriorityClass` énumération.  
  
|Nom convivial dans DTSPriorityClass|Valeur numérique|  
|---------------------------------------|-------------------|  
|Par défaut|0|  
|AboveNormal|1|  
|Normale|2|  
|BelowNormal|3|  
|Idle|4|  
  
 `ProtectionLevel` propriété, définie à l’aide de valeurs à partir de la `DTSProtectionLevel` énumération.  
  
|Nom convivial dans DTSProtectionLevel|Valeur numérique|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="PrecedenceConstraints"></a> Contraintes de précédence  
 `EvalOp` propriété, définie à l’aide de valeurs à partir de la `DTSPrecedenceEvalOp` énumération.  
  
|Nom convivial dans DTSPrecedenceEvalOp|Valeur numérique|  
|------------------------------------------|-------------------|  
|Expression|1|  
|Contrainte|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value` propriété, définie à l’aide de valeurs à partir de la `DTSExecResult` énumération.  
  
|Nom convivial|Valeur numérique|  
|-------------------|-------------------|  
|Réussi|0|  
|Failure|1|  
|Completion|2|  
|Opération annulée|3|  
  
##  <a name="Foreach"></a> Énumérateurs de boucles Foreach  
 La boucle Foreach inclut un jeu d'énumérateurs comportant des propriétés pouvant être définies par des expressions de la propriété.  
  
### <a name="foreach-ado-enumerator"></a>Énumérateur Foreach ADO  
 `Type` propriété, définie à l’aide de valeurs à partir de la `ADOEnumerationType` énumération.  
  
|Nom convivial dans ADOEnumerationType|Valeur numérique|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Énumérateur Foreach Nodelist  
 `SourceDocumentType`, `InnerXPathStringSourceType`, et **OuterXPathStringSourceType** propriétés — définie à l’aide de valeurs à partir de la `SourceType` énumération.  
  
|Nom convivial dans SourceType|Valeur numérique|  
|---------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `EnumerationType` propriété, définie à l’aide de valeurs à partir de la `EnumerationType` énumération.  
  
|Nom convivial dans EnumerationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|Navigator|0|  
|Nœud|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType` propriété, définie à l’aide de valeurs à partir de la `InnerElementType` énumération.  
  
|Nom convivial dans InnerElementType|Valeur numérique|  
|---------------------------------------|-------------------|  
|Navigator|0|  
|Nœud|1|  
|NodeText|2|  
  
##  <a name="Tasks"></a> Tâches  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut de nombreuses tâches avec des propriétés pouvant être définies par des expressions de la propriété.  
  
### <a name="analysis-services-execute-ddl-task"></a>Tâche DDL d'exécution de SQL Server Analysis Services  
 `SourceType` propriété, définie à l’aide de valeurs à partir de la `DDLSourceType` énumération.  
  
|Nom convivial dans DDLSourceType|Valeur numérique|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
### <a name="bulk-insert-task"></a>tâche d'insertion en bloc  
 `DataFileType` propriété, définie à l’aide de valeurs à partir de la `DTSBulkInsert_DataFileType` énumération.  
  
|Nom convivial dans DTSBulkInsert_DataFileType|Valeur numérique|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>Tâche d’exécution de requêtes SQL  
 `ResultSetType` propriété, définie à l’aide de valeurs à partir de la `ResultSetType` énumération.  
  
|Nom convivial dans ResultSetType|Valeur numérique|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType` propriété, définie à l’aide de valeurs à partir de la `SqlStatementSourceType` énumération.  
  
|Nom convivial dans SqlStatementSourceType|Valeur numérique|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|FileConnection|2|  
|Variable|3|  
  
### <a name="file-system-task"></a>Tâches du système de fichiers  
 `Operation` propriété, définie à l’aide de valeurs à partir de la `DTSFileSystemOperation` énumération.  
  
|Nom convivial dans DTSFileSystemOperation|Valeur numérique|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes` propriété, définie à l’aide de valeurs à partir de la `DTSFileSystemAttributes` énumération.  
  
|Nom convivial dans DTSFileSystemAttributes|Valeur numérique|  
|----------------------------------------------|-------------------|  
|Normale|0|  
|Archive|1|  
|Hidden|2|  
|En lecture seule|4|  
|Système|8|  
  
### <a name="ftp-task"></a>Tâche FTP  
 `Operation` propriété, définie à l’aide de valeurs à partir de la `DTSFTPOp` énumération.  
  
|Nom convivial dans DTSFTPOp|Valeur numérique|  
|-------------------------------|-------------------|  
|Send|0|  
|Recevoir|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType` propriété, définie à l’aide de valeurs à partir de la `MQMessageType` énumération.  
  
|Nom convivial dans MQMessageType|Valeur numérique|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType` propriété, définie à l’aide de valeurs à partir de la `MQStringMessageCompare` énumération.  
  
|Nom convivial dans MQStringMessageCompare|Valeur numérique|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType` propriété, définie à l’aide de valeurs à partir de la `MQType` énumération.  
  
|Nom convivial dans MQType|Valeur numérique|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>tache Envoyer un message  
 `MessageSourceType` propriété, définie à l’aide de valeurs à partir de la `SendMailMessageSourceType` énumération.  
  
|Nom convivial dans SendMailMessageSourceType|Valeur numérique|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
 `Priority` propriété, définie à l’aide de valeurs à partir de la `MailPriority` énumération.  
  
|Nom convivial dans MailPriority|Valeur numérique|  
|-----------------------------------|-------------------|  
|Élevée|1|  
|Normale|3|  
|Faible|5|  
  
### <a name="transfer-database-task"></a>Tâche de transfert de bases de données  
 `Action` propriété, définie à l’aide de valeurs à partir de la `TransferAction` énumération.  
  
|Nom convivial dans TransferAction|Valeur numérique|  
|-------------------------------------|-------------------|  
|Copier|0|  
|Déplacer|1|  
  
 `Method` propriété, définie à l’aide de valeurs à partir de la `TransferMethod` énumération.  
  
|Nom convivial dans TransferMethod|Valeur numérique|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>Tâche de transfert de messages d'erreur  
 `IfObjectExists` propriété, définie à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-jobs-task"></a>Tâche de transfert de travaux  
 `IfObjectExists` propriété, définie à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-logins-task"></a>Tâche de transfert de connexions  
 `IfObjectExists` propriété, définie à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
 `LoginsToTransfer` propriété, définie à l’aide de valeurs à partir de la `LoginsToTransfer` énumération.  
  
|Nom convivial dans LoginsToTransfer|Valeur numérique|  
|---------------------------------------|-------------------|  
|AllLogins|0|  
|SelectedLogins|1|  
|AllLoginsFromSelectedDatabases|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>Tâche de transfert de procédures stockées de master  
 `IfObjectExists` propriété, définie à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-sql-server-objects-task"></a>Tâche de transfert d'objets SQL Server  
 `ExistingData` propriété, définie à l’aide de valeurs à partir de la `ExistingData` énumération.  
  
|Nom convivial dans ExistingData|Valeur numérique|  
|-----------------------------------|-------------------|  
|Remplacer|0|  
|Append|1|  
  
### <a name="web-service-task"></a>Tâche de service Web  
 `OutputType` propriété, définie à l’aide de valeurs à partir de la `DTSOutputType` énumération.  
  
|Nom convivial dans DTSOutputType|Valeur numérique|  
|------------------------------------|-------------------|  
|Fichier|0|  
|Variable|1|  
  
### <a name="wmi-data-reader-task"></a>Tâche Lecteur de données WMI  
 `OverwriteDestination` propriété, définie à l’aide de valeurs à partir de la `OverwriteDestination` énumération.  
  
|Nom convivial dans OverwriteDestination|Valeur numérique|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType` propriété, définie à l’aide de valeurs à partir de la `OutputType` énumération.  
  
|Nom convivial dans OutputType|Valeur numérique|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType` propriété, définie à l’aide de valeurs à partir de la `DestinationType` énumération.  
  
|Nom convivial dans DestinationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `WqlQuerySourceType` propriété, définie à l’aide de valeurs à partir de la `QuerySourceType` énumération.  
  
|Nom convivial dans QuerySourceType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
 Propriété `ActionAtEvent` de l'Observateur d'événement WMI - définie à l'aide de valeurs provenant de l'énumération `ActionAtEvent`.  
  
|Nom convivial dans ActionAtEvent|Valeur numérique|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout` propriété, définie à l’aide de valeurs à partir de la `ActionAtTimeout` énumération.  
  
|Nom convivial dans ActionAtTimeout|Valeur numérique|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent` propriété, définie à l’aide de valeurs à partir de la `AfterEvent` énumération.  
  
|Nom convivial dans AfterEvent|Valeur numérique|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout` propriété, définie à l’aide de valeurs à partir de la `AfterTimeout` énumération.  
  
|Nom convivial dans AfterTimeout|Valeur numérique|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType` propriété, définie à l’aide de valeurs à partir de la `QuerySourceType` énumération.  
  
|Nom convivial dans QuerySourceType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
### <a name="xml-task"></a>Tâche XML  
 `OperationType` propriété, définie à l’aide de valeurs à partir de la `DTSXMLOperation` énumération.  
  
|Nom convivial dans DTSXMLOperation|Valeur numérique|  
|--------------------------------------|-------------------|  
|Valider|0|  
|XSLT|1|  
|XPATH|2|  
|Fusion|3|  
|Diff|4|  
|Patch|5|  
  
 Propriétés `SourceType`, `SecondOperandType` et `XPathSourceType` - définies à l'aide de valeurs provenant de l'énumération `DTSXMLSourceType`.  
  
|Nom convivial dans DTSXMLSourceType|Valeur numérique|  
|---------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `DestinationType` et **DiffGramDestinationType** propriétés — définie à l’aide de valeurs à partir de la `DTSXMLSaveResultTo` énumération.  
  
|Nom convivial dans DTSXMLSaveResultTo|Valeur numérique|  
|-----------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `ValidationType` propriété, définie à l’aide de valeurs à partir de la `DTSXMLValidationType` énumération.  
  
|Nom convivial dans DTSXMLValidationType|Valeur numérique|  
|-------------------------------------------|-------------------|  
|DTD|0|  
|XSD|1|  
  
 `XPathOperation` propriété, définie à l’aide de valeurs à partir de la `DTSXMLXPathOperation` énumération.  
  
|Nom convivial dans DTSXMLXPathOperation|Valeur numérique|  
|-------------------------------------------|-------------------|  
|Evaluation|0|  
|Valeurs|1|  
|NodeList|2|  
  
 `DiffOptions` propriété, définie à l’aide de valeurs à partir de la `DTSXMLDiffOptions` énumération. Les options dans cet énumérateur ne sont pas mutuellement exclusives. Pour utiliser plusieurs options, fournissez une liste des options à appliquer, séparées par des virgules.  
  
|Nom convivial dans DTSXMLDiffOptions|Valeur numérique|  
|----------------------------------------|-------------------|  
|None|0|  
|IgnoreChildOrder|1|  
|IgnoreComments|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|IgnoreNamespaces|16|  
|IgnorePrefixes|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm` propriété, définie à l’aide de valeurs à partir de la `DTSXMLDiffAlgorithm` énumération.  
  
|Nom convivial dans DTSXMLDiffAlgorithm|Valeur numérique|  
|------------------------------------------|-------------------|  
|Auto|0|  
|Rapide|1|  
|Précise|2|  
  
##  <a name="MaintenancePlanTasks"></a> Tâches du plan de maintenance  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut un ensemble de tâches qui effectuent des tâches SQL Server à utiliser dans des plans de maintenance et dans des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge la gestion de ces tâches par programmation et la documentation de référence de programmation n’inclut pas la documentation API de ces tâches et de leurs énumérateurs.  
  
### <a name="all-maintenance-tasks"></a>Toutes les tâches de maintenance  
 Toutes les tâches de maintenance utilisent les énumérations suivantes pour définir les propriétés spécifiées.  
  
 `DatabaseSelectionType` propriété, définie à l’aide de valeurs à partir de la `DatabaseSelection` énumération.  
  
|Nom convivial dans DatabaseSelection|Valeur numérique|  
|----------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Système|2|  
|Utilisateur|3|  
|Specific|4|  
  
 `TableSelectionType` propriété, définie à l’aide de valeurs à partir de la `TableSelection` énumération.  
  
|Nom convivial dans TableSelection|Valeur numérique|  
|-------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Specific|2|  
  
 `ObjectTypeSelection` propriété, définie à l’aide de valeurs à partir de la `ObjectType` énumération.  
  
|Nom convivial dans ObjectType|Valeur numérique|  
|---------------------------------|-------------------|  
|Table de charge de travail|0|  
|Affichage|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>Tâche Sauvegarder la base de données  
 `DestinationCreationType` propriété, définie à l’aide de valeurs à partir de la `DestinationType` énumération.  
  
|Nom convivial dans DestinationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|Auto|0|  
|Manuel|1|  
  
 `ExistingBackupsAction` propriété, définie à l’aide de valeurs à partir de la `ActionForExistingBackups` énumération.  
  
|Nom convivial dans ActionForExistingBackups|Valeur numérique|  
|-----------------------------------------------|-------------------|  
|Ajouter|0|  
|Remplacer|1|  
  
 `BackupAction` propriété, définie à l’aide de valeurs à partir de la `BackupTaskType` énumération. Cette propriété fonctionne avec la `BackupIsIncremental` propriété pour définir le type de sauvegarde que la tâche effectue.  
  
|Nom convivial dans BackupTaskType|Valeur numérique|  
|-------------------------------------|-------------------|  
|Base de données|0|  
|Fichiers|1|  
|Journal|2|  
  
 Propriété `BackupDevice` : définie à l'aide de valeurs provenant de l'énumération SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) `DeviceType`.  
  
|Nom convivial dans DeviceType|Valeur numérique|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Bande|1|  
|Fichier|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>Tâche de nettoyage de maintenance  
 `FileTypeSelected` propriété, définie à l’aide de valeurs à partir de la `FileType` énumération.  
  
|Nom convivial dans FileType|Valeur numérique|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType` propriété, définie à l’aide de valeurs à partir de la `TimeUnitType` énumération.  
  
|Nom convivial dans TimeUnitType|Valeur numérique|  
|-----------------------------------|-------------------|  
|Jour|0|  
|Week|1|  
|Month|2|  
|Année|3|  
  
### <a name="update-statistics-task"></a>Tâche Mettre à jour les statistiques  
 Propriété `UpdateType` : définie à l'aide de valeurs provenant de l'énumération SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) `StatisticsTarget`.  
  
|Nom convivial dans StatisticsTarget|Valeur numérique|  
|---------------------------------------|-------------------|  
|colonne|1|  
|Index|2|  
|All|3|  
  
##  <a name="CommonProperties"></a> Propriétés communes  
 Les packages, les tâches et les conteneurs de boucles Foreach, de boucles For et de séquences peuvent utiliser les énumérations suivantes pour définir les propriétés spécifiées.  
  
 `ForceExecutionResult` propriété, définie à l’aide de valeurs à partir de la `DTSForcedExecResult` énumération.  
  
|Nom convivial dans DTSForcedExecResult|Valeur numérique|  
|------------------------------------------|-------------------|  
|None|-1|  
|Réussi|0|  
|Failure|1|  
|Completion|2|  
  
 Propriété `IsolationLevel` - définie à l'aide de valeurs provenant de l'énumération `IsolationLevel` .NET Framework. Pour plus d’informations, consultez la bibliothèque de classes .NET Framework dans [MSDN Library](http://go.microsoft.com/fwlink?LinkId=17313).  
  
 `LoggingMode` propriété, définie à l’aide de valeurs à partir de la `DTSLoggingMode` énumération.  
  
|Nom convivial dans DTSLoggingMode|Valeur numérique|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|Activé|1|  
|Désactivé|2|  
  
 `TransactionOption` propriété, définie à l’aide de valeurs à partir de la `DTSTransactionOption` énumération.  
  
|Nom convivial dans DTSTransactionOption|Valeur numérique|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|Pris en charge|1|  
|Requis|2|  
  
## <a name="related-tasks"></a>Tâches associées  
 [Ajouter ou modifier une expression de propriété](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des Expressions de propriété dans des Packages](use-property-expressions-in-packages.md)   
 [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md)   
 [Conteneurs Integration Services](../control-flow/integration-services-containers.md)   
 [Tâches Integration Services](../control-flow/integration-services-tasks.md)   
 [Contraintes de précédence](../control-flow/precedence-constraints.md)  
  
  
