---
title: Configuration de l’intégration des Services Service (Service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- configuration files [Integration Services]
- service [Integration Services], configuring
- default configuration files
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
caps.latest.revision: 70
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 71a0436edf57e820b7e6b559814f65823d4390eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283675"
---
# <a name="configuring-the-integration-services-service-ssis-service"></a>Configuration du service Integration Services (Service SSIS)
    
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dépend d'un fichier de configuration pour ses paramètres. Par défaut, le nom de ce fichier de configuration est MsDtsSrvr.ini.xml, et le fichier se trouve dans le dossier %ProgramFiles%\Microsoft SQL Server\120\DTS\Binn.  
  
 Généralement, il n'est pas nécessaire d'apporter des modifications à ce fichier de configuration, ni de modifier l'emplacement par défaut du fichier. Cependant, si vos packages sont stockés dans une instance nommée ou une instance distante du [!INCLUDE[ssDE](../includes/ssde-md.md)]ou dans plusieurs instances du [!INCLUDE[ssDE](../includes/ssde-md.md)], vous devez modifier le fichier de configuration. De plus, si vous déplacez le fichier de configuration vers un emplacement autre que l'emplacement par défaut, vous devez modifier la clé de Registre qui spécifie l'emplacement de fichier.  
  
## <a name="configuration-file-contents"></a>Contenu du fichier de configuration  
 Lorsque vous installez [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], le processus d'installation crée et installe le fichier de configuration pour le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Ce fichier de configuration par défaut contient les paramètres suivants :  
  
-   Les packages reçoivent une commande d'arrêt lorsque le service s'arrête.  
  
-   Les dossiers racine à afficher pour [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sont les dossiers MSDB et File System.  
  
-   Les packages dans le système de fichiers qui le [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service gère se trouvent dans %ProgramFiles%\Microsoft SQL Server\120\DTS\Packages.  
  
 Ce fichier de configuration spécifie également quelle base de données msdb contient les packages que le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] gère. Par défaut, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est configuré pour gérer les packages dans la base de données msdb de l’instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] qui est installée au même moment que [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Si aucune instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] n’est installée au même moment, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est configuré pour gérer les packages dans la base de données msdb de l’instance locale par défaut du [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
### <a name="default-configuration-file-example"></a>Exemple de fichier de configuration par défaut  
 L'exemple suivant présente un fichier de configuration par défaut qui spécifie les paramètres suivants :  
  
-   Arrêt des packages exécutés si le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est arrêté.  
  
-   Les dossiers racine pour le stockage de package dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sont les dossiers MSDB et File System.  
  
-   Le service gère les packages qui sont stockés dans la base de données msdb de l'instance locale par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Le service gère des packages qui sont stockés dans le système de fichiers du dossier Packages.  
  
 **Exemple de fichier de configuration par défaut**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file"></a>Modification du fichier de configuration  
 Vous pouvez modifier le fichier de configuration de manière à permettre aux packages de poursuivre leur exécution en cas d'arrêt du service, à afficher des dossiers racine supplémentaires dans l'Explorateur d'objets ou à spécifier un dossier différent ou des dossiers supplémentaires dans le système de fichiers que doit gérer le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Par exemple, vous pouvez créer des dossiers racine supplémentaires de type `SqlServerFolder`, pour gérer les packages dans les bases de données msdb d’instances supplémentaires de [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
> [!NOTE]  
>  Certains caractères ne sont pas valides dans les noms de dossiers. Les caractères valides des noms de dossiers sont déterminés par la classe [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **System.IO.Path** et le champ **GetInvalidFilenameChars** . Le champ **GetInvalidFilenameChars** fournit un tableau de caractères propre à la plateforme, qui ne peuvent pas être spécifiés dans des arguments de chaîne de chemin transmis aux membres de la classe **Path** . Le jeu des caractères non valides peut varier selon le système de fichiers. En général, les caractères non valides sont le guillemet ("), le caractère « inférieur à » (<) et la barre verticale (|).  
  
 Cependant, pour gérer des packages stockés dans une instance nommée ou une instance distante du [!INCLUDE[ssDE](../includes/ssde-md.md)], vous devez modifier le fichier de configuration. Si vous ne mettez pas à jour le fichier de configuration, vous ne pouvez pas utiliser **l’Explorateur d’objets** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour consulter des packages stockés dans la base de données msdb sur l’instance nommée ou l’instance distante. Si vous essayez d'utiliser l' **Explorateur d'objets** pour consulter ces packages, le message d'erreur suivant apparaît :  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 Pour modifier le fichier de configuration pour le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , utilisez un éditeur de texte.  
  
> [!IMPORTANT]  
>  Après avoir modifié le fichier de configuration de service, vous devez redémarrer le service afin d'utiliser la configuration de service mise à jour.  
  
### <a name="modified-configuration-file-example"></a>Exemple de fichier de configuration modifié  
 L'exemple suivant illustre un fichier de configuration modifié pour [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Ce fichier concerne une instance nommée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] appelée `InstanceName` , située sur un serveur nommé `ServerName`.  
  
 **Exemple de fichier de configuration modifié pour une instance nommée de SQL Server**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file-location"></a>Modification de l'emplacement du fichier de configuration  
La clé de Registre **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\ServiceConfigFile** Spécifie l’emplacement et le nom pour la configuration du fichier [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service utilise. La valeur par défaut de la clé de Registre est **C:\Program Files\Microsoft SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**. Vous pouvez mettre à jour la valeur de la clé de Registre pour utiliser un nom et un emplacement différents pour le fichier de configuration. Notez que le numéro de version dans le chemin d’accès (120 pour SQL Server [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)]) varie selon la version de SQL Server. 
  
  
> [!CAUTION]  
>  La modification incorrecte du Registre peut entraîner de graves problèmes et nécessiter la réinstallation du système d'exploitation. [!INCLUDE[msCoName](../includes/msconame-md.md)] ne peut pas garantir que les problèmes résultant d’une modification incorrecte du Registre peuvent être résolus. Avant de modifier le Registre, sauvegardez toutes vos données importantes. Pour plus d'informations sur la méthode de sauvegarde, de restauration et de modification du Registre, consultez l'article [!INCLUDE[msCoName](../includes/msconame-md.md)] Description du Registre de Microsoft Windows [de la Base de connaissances](http://support.microsoft.com/kb/256986).  
  
 Lorsqu'il démarre, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] charge le fichier de configuration. Toute modification de l'entrée de Registre nécessite le redémarrage du service.  
  
  
