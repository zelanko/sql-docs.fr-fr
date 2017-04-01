---
title: "Audit local pour la collecte de commentaires d’utilisation de SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "02/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "dbe-security"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Audit local"
ms.assetid: a0665916-7789-4f94-9086-879275802cf3
caps.latest.revision: 8
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 7
---
# Audit local pour la collecte de commentaires d’utilisation de SQL Server
## Introduction

Microsoft SQL Server 2016 (SQL Server) contient des fonctionnalités Internet susceptibles de collecter et d’envoyer des informations relatives à votre ordinateur ou appareil (« informations standard sur l’ordinateur ») à Microsoft. Le composant d’audit local de la [collecte de commentaires d’utilisation de SQL Serve](http://support.microsoft.com/kb/3153756) écrit les données collectées par le service vers un dossier désigné, représentant les données (journaux) qui peuvent être envoyées à Microsoft. L’objectif de l’audit local est d’autoriser les clients à visualiser toutes les données collectées par Microsoft avec cette fonctionnalité, pour des raisons de conformité, de réglementation ou de validation de la confidentialité.  

Dans SQL Server 2016 CU2, l’audit local est configurable au niveau de l’instance de moteur de base de données SQL Server et Analysis Services (SSAS). L’audit local n’est pas encore activé pour SQL Server Integration Services (SSIS). Les autres composants SQL Server installés pendant la configuration et les outils SQL Server qui sont téléchargés ou installés après la configuration ne possèdent pas de fonctionnalité d’audit local pour la collecte de commentaires relatifs à l’utilisation. 

## Conditions préalables 

Les éléments suivants sont nécessaires pour activer l’audit local sur chaque instance SQL Server : 

1. L’instance est corrigée sur SQL Server 2016 RTM CU2 ou version supérieure. 

1. L’utilisateur doit être un administrateur système ou doit bénéficier d’un rôle ayant accès à l’ajout et à la modification de la clé de Registre, la création des dossiers, la gestion de la sécurité des dossiers et l’arrêter/le démarrage d’un service Windows.  

## Étapes de préconfiguration avant l’activation de l’audit local 

Avant d’activer l’audit local, un administrateur système doit :

1. Connaître le nom de l’instance SQL Server et le compte de connexion de service de télémétrie SQL Server CEIP. 

1. Configurer un nouveau dossier pour les fichiers d’audit local.

1. Accorder des autorisations pour le compte de connexion de service de télémétrie SQL Server CEIP.

1. Créer un paramètre de clé de Registre pour configurer le répertoire cible d’audit local. 

    Pour la création de la clé du moteur de base de données sur *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL13.\<INSTANCENAME\>\\CPE*. 
    
    Pour la création de la clé d’Analysis Services sur *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL13.\<INSTANCENAME\>\\CPE*.

### Obtenir le compte de connexion de service SQL Server CEIP

Procédez comme suit pour obtenir le compte de connexion de service de télémétrie SQL Server CEIP
 
1. Lancez **Services** ; cliquez sur le bouton **Windows** et tapez *services.msc*. 

2. Accédez au service approprié. Par exemple, pour le moteur de base de données, localisez le* nom de l’instance*** du **service SQL Server CEIP. Pour Analysis Services, localisez le *nom de l’instance*** **SQL Server Analysis Services CEIP. 

3. Cliquez avec le bouton droit sur le service et sélectionnez **Propriétés**. 

4. Cliquez sur l’onglet **Ouverture de session**. Le compte d’ouverture de session apparaît dans **Ce compte**. 

### Configurer un nouveau dossier pour les fichiers d’audit local.    

Créez un dossier (répertoire d’audit local) où l’audit local écrit les journaux. Par exemple, le chemin d’accès complet au répertoire d’audit local pour une instance par défaut du moteur de base de données serait : *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\*. 
 
> Remarque : configurez le chemin d’accès du répertoire pour l’audit local à l’extérieur du chemin d’installation de SQL Server pour éviter que l’autorisation des fonctionnalités d’audit et de la correction entraîne des problèmes éventuels avec SQL Server.

  ||Décision de conception|Recommandation|  
  |------|-----------------|----------|  
  |![Checkbox](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|Disponibilité de l’espace |Pour une charge de travail modérée avec 10 bases de données environ, prévoyez environ 2 Mo d’espace disque par jour et par instance.|  
|![Checkbox](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|Répertoires distincts | Créez un répertoire pour chaque instance. Par exemple, utilisez *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\* pour une instance SQL Server nommée `MSSQLSERVER`. Cela simplifie la gestion des fichiers.
|![Checkbox](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|Dossiers séparés |Utilisez un dossier spécifique pour chaque service. Par exemple, pour un nom d’instance donné, vous devez avoir un dossier pour le moteur de base de données. Si une instance SSAS utilise le même nom d’instance, créez un dossier distinct pour SSAS. Lorsque le moteur de base de données et les instances Analysis Services sont configurés dans le même dossier, l’audit local écrit dans le même fichier journal pour les deux instances.| 
|![Checkbox](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|Accorder des autorisations pour le compte de connexion de service de télémétrie SQL Server CEIP|Activer l’option **Lister le contenu des dossiers**, et l’accès **En lecture** et **En écriture** au compte de connexion de service de télémétrie SQL Server CEIP|


### Accorder des autorisations pour le compte de connexion de service de télémétrie SQL Server CEIP
  
1. Dans **l’Explorateur de fichiers**, accédez à l’emplacement où se trouve le nouveau dossier.  

1. Cliquez avec le bouton droit sur le nom du dossier, puis sélectionnez **Propriétés**. 

1. Sous l’onglet **Sécurité**, cliquez sur **Modifier**, puis gérez l’autorisation.

1. Cliquez sur **Ajouter** et tapez les informations d’identification du service de télémétrie SQL Server CEIP, par exemple `NT Service\SQLTELEMETRY`.   

1. Cliquez sur **Vérifier les noms** pour valider le nom fourni, puis cliquez sur **OK**. 

1. Dans la boîte de dialogue **Autorisation**, choisissez le compte de connexion au service de télémétrie SQL Server CEIP, et cliquez sur **Lister le contenu des dossiers**, **En lecture** et **En écriture**.  

1. Cliquez sur **OK** pour appliquer les modifications d’autorisation immédiatement. 
  
### Créer un paramètre de clé de Registre pour configurer le répertoire cible d’audit local.

1. Lancez regedit.  

1. Accédez au chemin d’accès CPE approprié. 

    Pour l’utilisation du moteur de base de données *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL13.\<INSTANCENAME\>\\CPE*. 
    
    Pour l’utilisation d’Analysis Services *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS13.\<INSTANCENAME\>\\CPE*.

1. Cliquez avec le bouton droit sur le chemin d’accès CPE et choisissez **Nouveau**. Cliquez sur **Valeur de chaîne**.

1. Nommez la nouvelle clé de Registre `UserRequestedLocalAuditDirectory`. 
 
## Activation ou désactivation de l’audit local

Après avoir effectué les étapes de préconfiguration, vous pouvez activer l’audit local. Pour ce faire, utilisez un compte d’administrateur système ou un rôle similaire avec accès à la modification des clés de Registre pour activer ou désactiver l’audit local en suivant les étapes ci-dessous. 

1. Lancez **regedit**.  

1. Accédez au chemin d’accès CPE approprié. 

    Pour l’utilisation du moteur de base de données *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL13.\<INSTANCENAME\>\\CPE*. 
    
    Pour l’utilisation d’Analysis Services *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS13.\<INSTANCENAME\>\\CPE*.

1. Cliquez avec le bouton droit sur **UserRequestedLocalAuditDirectory**, puis sur *Modifier*. 

1. Pour activer l’audit local, tapez le chemin d’accès d’audit local, par exemple *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\*.
 
    Pour désactiver l’audit local, effacez la valeur dans **UserRequestedLocalAuditDirectory**.

1. Fermez **regedit**. 

SQL Server CEIP doit reconnaître le paramètre d’audit local immédiatement si le service est déjà en cours d’exécution. Pour démarrer le service SQL Server CEIP, l’administrateur système ou une personne ayant accès au démarrage ou à l’arrêt des services Windows peut suivre les étapes ci-dessous : 

1. Lancez l’application Services, en cliquant sur le bouton Windows et tapez Services. 

1. Accédez au service approprié. 

    Pour le moteur de base de données, utilisez **Service SQL Server CEIP (\<INSTANCENAME\>)**. 
    
    Pour Analysis Services, utilisez **SQL Server Analysis Services CEIP (\<INSTANCENAME\>)**. 

1. Cliquez avec le bouton droit sur le service et sélectionnez Redémarrer. 

1. Vérifiez que l’état du service est **En cours d’exécution**. 

L’audit local va générer un fichier journal par jour. Les fichiers journaux seront au format `<YYYY-MM-DD>.json`. Par exemple, *2016-07-12.json*. Si un fichier existe déjà pour le jour dans le répertoire désigné, l’audit local va s’y ajouter. Dans le cas contraire, il créera un fichier pour le jour en question. 

> Remarque : après avoir activé l’audit local, 5 minutes peuvent être nécessaires pour la première écriture du fichier journal. 

## Maintenance 

1. Pour limiter l’utilisation de l’espace disque par les fichiers écrits par l’audit local, configurez une stratégie ou une tâche régulière pour nettoyer le répertoire d’audit local afin de supprimer les fichiers anciens et inutiles.  

2. Sécurisez le chemin d’accès du répertoire d’audit local afin qu’il soit accessible uniquement par les personnes concernées. Notez que les fichiers journaux contiennent des informations comme indiqué dans [Configurer SQL Server 2016 pour envoyer des commentaires à Microsoft](http://support.microsoft.com/kb/3153756). L’accès à ce fichier doit être configuré pour empêcher la plupart des membres de votre organisation de le lire.  

## Dictionnaire de données de la structure de données de sortie d’audit local 

- Les fichiers journaux d’audit local sont au format JSON, contenant un ensemble d’objets (lignes) représentant des points de données qui sont envoyés à Microsoft à **emitTime**.  

- Chaque ligne suit un schéma spécifique identifié par **schemaVersion**.   

- Chaque ligne est une sortie d’une session de service SQLCEIP identifiée comme **sessionID**.  

- Les lignes sont émises dans l’ordre identifié par **sequence**. 

- Chaque ligne de point de données contient la sortie d’un **queryIdentifier** qui peut être une requête T-SQL, une session XE ou un message lié à un type de trace, identifié comme **traceName**.   

- Les **queryIdentifiers** sont regroupés et un contrôle de version leur est affecté avec **querySetVersion**. 

- **data** contient la sortie de l’exécution de la requête correspondante qui a pris **queryTimeInTicks**. 

- Les **queryIdentifiers** pour les requêtes T-SQL ont la définition de la requête T-SQL stockée dans la requête. 


| Hiérarchie logique des informations d’audit local | Colonnes associées |
| ------ | -------|
| En-tête | emitTime, schemaVersion 
| Machine | hostname, domainHash, sqmID, operatingSystem 
| Instance | instanceName, correlationID, clientVersion 
| Session | sessionID, traceName 
| Requête | sequence, querySetVersion, queryIdentifier, query, queryTimeInTicks 
| Données |  données 

### Définition et exemples des paires nom/valeur 

Les colonnes répertoriées ci-dessous représentent l’ordre de la sortie du fichier d’audit local. Le hachage à sens unique avec SHA 256 est utilisé pour les valeurs anonymes pour certaines colonnes ci-dessous.  

| Nom | Description | Exemples de valeurs
|-------|--------| ----------|
|hostname | Nom de la machine anonyme sur laquelle SQL Server est installé| de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|domainHash| Hachage du domaine anonyme de la machine hébergeant l’instance SQL Server | de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|sqmId |Identificateur représentant la machine sur laquelle SQL Server est installé | 02AF58F5-753A-429C-96CD-3900E90DB990 
|instanceName| Nom anonyme de l’instance SQL Server| e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 
|SchemaVersion| Version du schéma de SQLCEIP |  3 
|emitTime |Heure d’émission UTC du point de données | 2016-09-08T17:20:22.1124269Z 
|sessionId | Identificateur de session pour la maintenance du service SQLCEIP | 89decf9a-ad11-485c-94a7-fefb3a02ed86 
| correlationId | Espace réservé pour un identificateur supplémentaire | 0 
|séquence | Numéro de séquence des points de données envoyés au sein de la session | 15 
| clientVersion | Version d’instance SQL Server | 13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223) 
| operatingSystem | La version du système d’exploitation sur lequel l’instance SQL Server est installée | Microsoft Windows Server 2012 R2 Datacenter 
| querySetVersion | Version d’un groupe de définitions de requête | 1.0.0.0 
|traceName | Catégories de traces : (SQLServerXeQueries, SQLServerPeriodicQueries, SQLServerOneSettingsException) | SQLServerPeriodicQueries 
|queryIdentifier | Un identificateur de la requête | SQLServerProperties.002 
|données   | La sortie des informations collectées sur queryIdentifier en tant que sortie de requête T-SQL, de session XE ou de l’application |   [{"Collation": "SQL_Latin1_General_CP1_CI_AS","SqlFTinstalled": "0" "SqlIntSec": "1","IsSingleUser": "0","SqlFilestreamMode": "0","SqlPbInstalled": "0","SqlPbNodeRole": "","SqlVersionMajor": "13","SqlVersionMinor": "0","SqlVersionBuild": "2161","ProductBuildType": "","ProductLevel": "RTM","ProductUpdateLevel": "CU2","ProductUpdateReference": "KB3182270","ProductRevision": "3","SQLEditionId": "-1534726760","IsClustered": "0","IsHadrEnabled": "0","SqlAdvAInstalled": "0","PacketReceived": "1210","Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tÉdition Standard (64 bits) sur Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"}],
|requête| Le cas échéant, la définition de requêtes T-SQL liée au queryIdentifier qui génère des données.        Ce composant n’est pas téléchargé par le service SQL Server CEIP. Il est inclus dans l’audit local en tant que référence pour les clients uniquement.| SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version
|queryTimeInTicks | La durée nécessaire à l’exécution de la requête avec la catégorie de trace suivante : (SQLServerXeQueries, SQLServerPeriodicQueries) |  0 
 
### Catégories de trace 
Actuellement, nous collectons les catégories de trace suivantes : 

- **SQLServerXeQueries** : contient les points de données collectés via la session d’événements étendus. 

- **SQLServerPeriodicQueries** : contient les points de données collectés via les requêtes périodiques exécutées dans une instance SQL Server. 

- **SQLServerPerDBPeriodicQueries** : contient les points de données collectés via les requêtes périodiques exécutées sur 30 bases de données maximum dans une instance SQL Server. 

- **SQLServerOneSettingsException** : contient les messages d’exception liés à la mise à jour du jeu de schéma et/ou du jeu de requêtes. 

- **DigitalProductID** : contient les points de pour l’agrégation d’ID de produits numériques hachés (SHA-256) anonymes d’instances SQL Server. 

### Exemples de fichiers d’audit local



Voici un extrait d’une sortie de fichier JSON d’audit local.

```JSON
{
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:22.1124269Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 15,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "SQLServerProperties.002",
    "data": [
      {
        "Collation": "SQL_Latin1_General_CP1_CI_AS",
        "SqlFTinstalled": "0",
        "SqlIntSec": "1",
        "IsSingleUser": "0",
        "SqlFilestreamMode": "0",
        "SqlPbInstalled": "0",
        "SqlPbNodeRole": "",
        "SqlVersionMajor": "13",
        "SqlVersionMinor": "0",
        "SqlVersionBuild": "2161",
        "ProductBuildType": "",
        "ProductLevel": "RTM",
        "ProductUpdateLevel": "CU2",
        "ProductUpdateReference": "KB3182270",
        "ProductRevision": "3",
        "SQLEditionId": "-1534726760",
        "IsClustered": "0",
        "IsHadrEnabled": "0",
        "SqlAdvAInstalled": "0",
        "PacketReceived": "1210",
        "Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tStandard Edition (64-bit) on Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"
      }
    ],
    "query": "SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version",
    "queryTimeInTicks": 0
  } ,
  {
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:24.9819144Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 61,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "ExternalScriptStats.001",
    "data": [
      {
        "counter_name": "Total Executions                                                                                                                ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Parallel Executions                                                                                                             ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Streaming Executions                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "SQL CC Executions                                                                                                               ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Implied Auth. Logins                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Total Execution Time (ms)                                                                                                       ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Execution Errors                                                                                                                ",
        "cntr_value": "0"
      }
    ],  
    "query": "select counter_name, cntr_value from sys.dm_os_performance_counters where object_name like \u0027%External Scripts%\u0027",
    "queryTimeInTicks": 155834
  } 
```
## Forum Aux Questions (FAQ)

**Comment les DBA lisent-ils les fichiers journaux d’audit local ?**
Ces fichiers journaux sont écrits au format JSON. Chaque ligne est un objet JSON qui représente un élément de télémétrie chargé auprès de Microsoft. Les noms de champs doivent être explicites. 

**Que se passe-t-il si le DBA désactive la collecte de commentaires d’utilisation ?**
Aucun fichier d’audit local ne sera écrit. 

**Que se passe-t-il en cas d’absence de connectivité Internet ou de machine derrière le pare-feu ?**
Les commentaires d’utilisation de SQL Server 2016 ne seront pas envoyés à Microsoft. Une tentative d’écriture des journaux d’audit local sera effectuée si la configuration est correcte.

**Comment les DBA désactivent-ils l’audit local ?**
Supprimez l’entrée de clé de Registre UserRequestedLocalAuditDirectory.

**Qui peut lire les fichiers journaux d’audit local ?**
Toute personne de votre organisation ayant accès au répertoire d’audit local.

**Comment les DBA gèrent-ils les fichiers journaux écrits dans le répertoire désigné ?**
Les DBA devront gérer eux-mêmes le nettoyage des fichiers dans le répertoire pour éviter de consommer trop d’espace disque.

**Y a-t-il un client ou un outil que je peux utiliser pour lire cette sortie JSON ?**
Le résultat peut être lu avec le Bloc-notes, Visual Studio ou tout lecteur JSON de votre choix.
Vous pouvez également lire le fichier JSON et analyser les données dans une instance SQL Server 2016, comme illustré ci-dessous. Pour plus d’informations sur la lecture de fichiers JSON dans SQL Server, visitez [Importation de fichiers JSON dans SQL Server à l’aide de OPENROWSET (BULK) et OPENJSON (Transact-SQL)](http://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/10/07/bulk-importing-json-files-into-sql-server/).

```Transact-SQL
DECLARE @JSONFile AS VARCHAR(MAX)

-- Read the JSON file into variable 
SELECT @JSONFile = BulkColumn 
FROM OPENROWSET (BULK 'C:\SQLCEIPAudit\MSSQLSERVER\2016-09-08.json', SINGLE_CLOB) MyFile 

-- Check if the JSON file has been read properly and if it's in a JSON format
SELECT 
    @JSONFile LocalAuditOutput, 
    ISJSON(@JSONFile) IsFileInJSONFormat

-- Get the query identifier, query and the data (output of the query)   
SELECT 
    sequence,
    queryIdentifier,
    query,
    data
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON)
-- Get specific details about the output of "DatabaseProperties.001" query  
SELECT 
    QueryIdentifier,
    DatabaseID,
    CompatibilityLevel,
    IsQueryStoreOn
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON) 
    CROSS APPLY OPENJSON(data) 
        WITH (   DatabaseID varchar(128) '$.database_id'
                ,CompatibilityLevel varchar(128) '$.compatibility_level'
                ,IsQueryStoreOn varchar(128) '$.QS'
             )
WHERE queryIdentifier = 'DatabaseProperties.001'
```
