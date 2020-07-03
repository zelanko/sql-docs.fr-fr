---
title: Gérer les fichiers journaux DQS
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: swinarko
ms.author: sawinark
ms.openlocfilehash: e4b5864129d25754fb2177376e011be1972078e1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898127"
---
# <a name="manage-dqs-log-files"></a>Gérer les fichiers journaux DQS

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Les fichiers journaux[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) vous aident dans le diagnostic et la résolution de problèmes avec [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]et [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]. Des fichiers journaux distincts sont générés pour [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]et [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].  
  
 Vous pouvez utiliser [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] pour configurer le paramètre de gravité du journal pour les fonctionnalités et les modules [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . En outre, vous pouvez également configurer d'autres paramètres (avancés) pour les fichiers journaux DQS en modifiant manuellement les paramètres de configuration des journaux DQS dans la base de données DQS_MAIN et un fichier XML sur l'ordinateur [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] .  
  
##  <a name="data-quality-server-log-file"></a><a name="DQSServer"></a>Fichier journal du serveur de qualité des données  
 Le fichier journal [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , DQServerLog.DQS_MAIN.log, inclut les enregistrements des activités exécutées sur [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Si vous avez installé l’instance par défaut de SQL Server, le fichier DQServerLog.DQS_MAIN.log est disponible dans C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log. Le fichier journal [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] contient les informations suivantes, chacune délimitée par une barre verticale (|) :  
  
-   Date et heure  
  
-   Nom du thread  
  
-   ID du thread  
  
-   Gravité de l'enregistrement (FATAL, ERROR, WARN, INFO et DEBUG)  
  
    > [!NOTE]  
    >  La gravité DEBUG est identique à Commentaires.  
  
-   UID (ID infrastructure DQS interne)  
  
-   Espace de noms  
  
-   Classe et méthode  
  
-   Message  
  
 Outre ces informations, le fichier journal affiche aussi des informations sur la version de l'application, le nom de l'ordinateur, le nom d'utilisateur et le système d'exploitation.  
  
 Un exemple d'entrée du fichier journal [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] se présente comme suit :  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 Le fichier DQServerLog.DQS_MAIN.log est un fichier de restauration et un nouveau fichier journal est créé une fois que le fichier journal existant dépasse la limite de la taille du fichier par progression spécifiée dans les paramètres de configuration du journal [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . Pour plus d'informations, consultez [Configure Advanced Settings for DQS Log Files](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="data-quality-client-log-file"></a><a name="DQSClient"></a>Fichier journal Data Quality Client  
 Le fichier journal [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , DQClientLog.log, inclut les enregistrements côté client. Le fichier journal [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] est disponible à %APPDATA%\SSDQS\Log. Le fichier journal [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] contient un ensemble d'informations similaires à celles du fichier journal du serveur, mais pour le côté client.  
  
 Comme pour le fichier journal [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , le fichier journal [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] est aussi un fichier par progression et un nouveau fichier journal est créé une fois que le fichier journal existant dépasse la limite de la taille du fichier par progression spécifiée dans les paramètres de configuration du journal [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Pour plus d'informations, consultez [Configure Advanced Settings for DQS Log Files](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="dqs-cleansing-component-log-file"></a><a name="DQSCleansing"></a>Fichier journal du composant de nettoyage DQS  
 Le fichier journal [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] , DQSSSISLog.log, inclut les enregistrements des activités effectuées à l'aide de [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]. Le fichier journal du composant [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] est disponible à %APPDATA%\SSDQS\Log. Le fichier journal [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] contient un ensemble d'informations similaires à celles du fichier journal du serveur, mais pour le [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].  
  
##  <a name="related-tasks"></a><a name="RT"></a> Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment configurer les paramètres de gravité du journal pour les fichiers journaux DQS avec [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].|[Configurer les niveaux de gravité pour les fichiers journaux DQS](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|Explique comment configurer manuellement les paramètres avancés des fichiers journaux DQS.|[Configurer les paramètres avancés pour les fichiers journaux DQS](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [administration de dqs](../data-quality-services/dqs-administration.md)  
  
  
