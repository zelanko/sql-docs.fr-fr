---
title: Configurer les paramètres avancés pour les fichiers journaux DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- log files,advanced settings
- dqs log files,advanced settings
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 998f1079044f530a824600fede88c99ca91f793e
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85886043"
---
# <a name="configure-advanced-settings-for-dqs-log-files"></a>Configurer les paramètres avancés pour les fichiers journaux DQS
  Cette rubrique explique comment configurer les paramètres avancés pour [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] et les fichiers journaux [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , tels que la définition de la limite de la taille des fichiers par progression des fichiers journaux, la définition du modèle d'horodatage les événements, etc.  
  
> [!NOTE]  
>  Ces activités ne peuvent pas être effectuées à l'aide de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]et sont réservées aux utilisateurs expérimentés uniquement.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
  
-   Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe sysadmin dans l'instance SQL Server afin de pouvoir modifier les paramètres de configuration dans la table A_CONFIGURATION de la base de données DQS_MAIN.  
  
-   Vous devez être connecté en tant que membre du groupe Administrateurs sur l'ordinateur où vous modifiez le fichier DQLog.Client.xml pour configurer les paramètres de journalisation [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] .  
  
##  <a name="configure-data-quality-server-log-settings"></a><a name="DQSServer"></a> Configurer les paramètres des journaux du serveur de qualité des données  
 Les paramètres des journaux [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] sont présents au format XML dans la colonne **VALUE** de la ligne **ServerLogging** de la table A_CONFIGURATION de la base de données DQS_MAIN. Vous pouvez exécuter la requête SQL suivante pour afficher les informations de configuration :  
  
```sql  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'; 
```  
  
 Vous devez mettre à jour les informations appropriées dans la colonne **VALUE** de la ligne **ServerLogging** pour modifier les paramètres de configuration de la journalisation [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . Dans cet exemple, nous mettrons à jour les paramètres des journaux [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] pour définir la limite de la taille des fichiers par progression à 25 000 Ko (valeur par défaut 20 000 Ko).  
  
1.  Démarrez Microsoft SQL Server Management Studio et connectez-vous à l'instance de SQL Server appropriée.  
  
2.  Dans l'Explorateur d'objets, cliquez avec le bouton droit sur le serveur, puis cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre Éditeur de requête, copiez les instructions SQL suivantes :  
  
    ```sql  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  Appuyez sur F5 pour exécuter les instructions. Vérifiez le volet **résultats** pour vérifier que les instructions ont été exécutées avec succès.  
  
5.  Pour appliquer les modifications effectuées à la configuration de journalisation [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , vous devez exécuter les instructions Transact-SQL suivantes. Ouvrez une nouvelle fenêtre de l'Éditeur de requête, puis collez les instructions Transact-SQL suivantes :  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
    ```  
  
6.  Appuyez sur F5 pour exécuter les instructions. Vérifiez le volet **résultats** pour vérifier que les instructions ont été exécutées avec succès.  
  
> [!NOTE]  
>  La configuration des paramètres de journalisation [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] est générée dynamiquement et stockée dans le fichier DQS_MAIN.Log, généralement disponible dans C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log si vous avez installé l'instance par défaut de SQL Server. Toutefois, les modifications apportées directement dans ce fichier ne se conservent pas et sont remplacées par les paramètres de configuration de la table A_CONFIGURATION de la base de données DQS_MAIN.  
  
##  <a name="configure-data-quality-client-log-settings"></a><a name="DQSClient"></a>Configurer les paramètres du journal Data Quality Client  
 Le [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fichier de configuration du paramètre de journal, DQLog.Client.xml, est généralement disponible dans C:\Program Files\Microsoft SQL Server\120\Tools\Binn\DQ\config. Le contenu du fichier XML est semblable au fichier XML que vous avez modifié précédemment pour les [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] paramètres de configuration du journal. Pour configurer les paramètres des journaux [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] :  
  
1.  Exécutez l'outil d'édition XML ou le Bloc-notes en tant qu'administrateur.  
  
2.  Ouvrez le fichier DQLog.Client.xml dans l'outil ou le Bloc-notes.  
  
3.  Apportez les modifications requises et enregistrez le fichier pour appliquer les nouvelles modifications de journalisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les niveaux de gravité pour les fichiers journaux DQS](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  
