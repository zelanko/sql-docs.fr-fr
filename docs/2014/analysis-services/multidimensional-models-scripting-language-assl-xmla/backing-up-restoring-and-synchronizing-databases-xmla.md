---
title: Sauvegarde, restauration et synchronisation des bases de données (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- restoring databases [XML for Analysis]
- backing up databases [XML for Analysis]
- database backups [XML for Analysis]
- synchronization [XML for Analysis]
- database restores [XML for Analysis]
ms.assetid: 6c021b2e-6ad0-444e-b23f-4b5f72ce084b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6163a538c4e8872016f7ec572e4c177cfe92de94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702275"
---
# <a name="backing-up-restoring-and-synchronizing-databases-xmla"></a>Sauvegarde, restauration et synchronisation de bases de données (XMLA)
  XML for Analysis propose trois commandes qui permettent de sauvegarder, restaurer et synchroniser des bases de données :  
  
-   La [commande Backup](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) sauvegarde une [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données à l' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aide d’un fichier de sauvegarde (. ABF), comme décrit dans la section [sauvegarde des bases de données](#backing_up_databases).  
  
-   La commande [Restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) restaure une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données à partir d’un fichier. ABF, comme décrit dans la section [restauration de bases de données](#restoring_databases).  
  
-   La commande [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) synchronise une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données avec les données et les métadonnées d’une autre base de données, comme décrit dans la section synchronisation des [bases de](#synchronizing_databases)données.  
  
##  <a name="backing_up_databases"></a>Sauvegarde des bases de données  
 Comme nous l'avons mentionné précédemment, la commande `Backup` permet de sauvegarder une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans un fichier de sauvegarde. La commande `Backup` possède plusieurs propriétés qui permettent de spécifier la base de données à sauvegarder, le fichier de sauvegarde à utiliser, le mode de sauvegarde des définitions de sécurité, ainsi que les partitions distantes à sauvegarder.  
  
> [!IMPORTANT]  
>  Le compte de service Analysis Services doit avoir l'autorisation d'écrire dans l'emplacement de sauvegarde spécifié pour chaque fichier. Par ailleurs, l'utilisateur doit avoir l'un des rôles suivants : rôle d'administrateur sur l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou membre d'un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à sauvegarder.  
  
### <a name="specifying-the-database-and-backup-file"></a>Spécification de la base de données et du fichier de sauvegarde  
 Pour spécifier la base de données à sauvegarder, vous devez définir la [](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) propriété de l’objet `Backup` de la commande. La propriété `Object` doit contenir un identificateur d'objet pour une base de données. Sinon, une erreur se produit.  
  
 Pour spécifier le fichier qui doit être créé et utilisé par le processus de sauvegarde, vous devez définir la propriété [file](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/file-element-xmla) de `Backup` la commande. La propriété `File` doit indiquer le chemin d'accès UNC et le nom du fichier de sauvegarde à créer.  
  
 En plus de spécifier le fichier à utiliser pour la sauvegarde, vous pouvez définir les options suivantes pour ce même fichier :  
  
-   Si vous affectez [](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/allowoverwrite-element-xmla) la valeur true à la propriété `Backup` AllowOverwrite, la commande remplace le fichier de sauvegarde si le fichier spécifié existe déjà. Si vous définissez la propriété `AllowOverwrite` à false, une erreur se produit si le fichier de sauvegarde spécifié existe déjà.  
  
-   Si vous affectez la valeur true à la propriété [ApplyCompression](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/applycompression-element-xmla) , le fichier de sauvegarde est compressé après la création du fichier.  
  
-   Si vous affectez à la propriété [Password](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/password-element-xmla) une valeur non vide, le fichier de sauvegarde est chiffré à l’aide du mot de passe spécifié.  
  
    > [!IMPORTANT]  
    >  Si les propriétés `ApplyCompression` et `Password` ne sont pas spécifiées, le fichier de sauvegarde stocke les noms et mots de passe utilisateur contenus dans les chaînes de connexion en texte clair. Les données stockées en texte en clair peuvent être récupérées. Pour plus de sécurité, utilisez les paramètres `ApplyCompression` et `Password` pour à la fois compresser et chiffrer le fichier de sauvegarde.  
  
### <a name="backing-up-security-settings"></a>Sauvegarde des paramètres de sécurité  
 La propriété de [sécurité](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla) détermine si `Backup` la commande sauvegarde les définitions de sécurité, telles que les rôles et les autorisations, définies [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur une base de données. La propriété `Security` détermine également si le fichier de sauvegarde inclut les comptes et groupes d'utilisateurs Windows définis comme membres des définitions de sécurité.  
  
 La valeur de la propriété `Security` est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*SkipMembership*|Inclut les définitions de sécurité dans le fichier de sauvegarde mais exclut les informations d'appartenance.|  
|*CopyAll*|Inclut les définitions de sécurité et les informations d'appartenance dans le fichier de sauvegarde.|  
|*IgnoreSecurity*|Exclut les définitions de sécurité du fichier de sauvegarde.|  
  
### <a name="backing-up-remote-partitions"></a>Sauvegarde de partitions distantes  
 Pour sauvegarder des partitions distantes de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous devez définir la propriété [BackupRemotePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/backupremotepartitions-element-xmla) de la commande `Backup` à true. Ce paramètre ordonne à la commande `Backup` de créer un fichier de sauvegarde distant pour chaque source de données distante utilisée pour stocker les partitions distantes de la base de données.  
  
 Pour chaque source de données distante à sauvegarder, vous pouvez spécifier son fichier de sauvegarde correspondant en incluant un élément [location](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/location-element-xmla) dans la propriété [locations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/locations-element-xmla) de `Backup` la commande. La `Location` `File` propriété de l’élément doit être définie sur le chemin d’accès UNC et le nom de fichier du fichier de sauvegarde distant, et sa propriété [DataSourceID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) définie sur l’identificateur de la source de données distante définie dans la base de données.  
  
##  <a name="restoring_databases"></a>Restauration de bases de données  
 La commande `Restore` permet de restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] spécifiée à partir d'un fichier de sauvegarde. La commande `Restore` comporte plusieurs propriétés qui permettent de spécifier la base de données à restaurer, le fichier de sauvegarde à utiliser, le mode de restauration des définitions de sécurité, les partitions distantes à stocker, ainsi que le déplacement d'objets ROLAP (Relational OLAP).  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], l'utilisateur doit avoir l'un des rôles suivants : être membre du rôle serveur pour l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou membre d'un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
> [!NOTE]  
>  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
### <a name="specifying-the-database-and-backup-file"></a>Spécification de la base de données et du fichier de sauvegarde  
 La propriété `DatabaseName` de la commande `Restore` doit contenir un identificateur d'objet pour une base de données. Sinon, une erreur se produit. Si la base de données spécifiée existe déjà, la propriété `AllowOverwrite` détermine si la base de données existante est remplacée. Si la propriété `AllowOverwrite` est définie à false et que la base de données spécifiée existe déjà, une erreur se produit.  
  
 La propriété `File` de la commande `Restore` doit indiquer le chemin d'accès UNC et le nom du fichier de sauvegarde à restaurer dans la base de données spécifiée. Vous pouvez également définir la propriété `Password` pour le fichier de sauvegarde spécifié. Si la propriété `Password` indique une valeur non vierge, le fichier de sauvegarde est déchiffré avec le mot de passe spécifié. Si le fichier de sauvegarde n'a pas été chiffré ou si le mot de passe spécifié ne correspond pas au mot de passe utilisé pour chiffrer le fichier de sauvegarde, une erreur se produit.  
  
### <a name="restoring-security-settings"></a>Restauration des paramètres de sécurité  
 La propriété `Security` détermine si la commande `Restore` restaure les définitions de sécurité, telles que les rôles et les autorisations, définies dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La propriété `Security` détermine également si la commande `Restore` inclut les comptes et les groupes d'utilisateurs Windows définis comme membres des définitions de sécurité dans le cadre du processus de restauration.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*SkipMembership*|Inclut les définitions de sécurité dans la base de données mais exclut les informations d'appartenance.|  
|*CopyAll*|Inclut les définitions de sécurité et les informations d'appartenance dans la base de données.|  
|*IgnoreSecurity*|Exclut les définitions de sécurité de la base de données.|  
  
### <a name="restoring-remote-partitions"></a>Restaration de partitions distantes  
 Pour chaque fichier de sauvegarde distant créé par une commande `Backup` précédente, vous pouvez restaurer sa partition distante associée en incluant un élément `Location` dans la propriété `Locations` de la commande `Restore`. La propriété [DataSourceType](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) de chaque `Location` élément doit être exclue ou explicitement définie sur *distant*.  
  
 Pour chaque élément `Location` spécifié, l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contacte la source de données distante spécifiée dans la propriété `DataSourceID` pour restaurer les partitions définies dans le fichier de sauvegarde distant spécifié dans la propriété `File`. Outre les propriétés `DataSourceID` et `File`, les propriétés suivantes sont disponibles pour chaque élément `Location` utilisé pour restaurer une partition distante :  
  
-   Pour remplacer la chaîne de connexion de la source de données distante spécifiée dans `DataSourceID`, vous pouvez définir une chaîne de connexion différente dans la propriété `ConnectionString` de l'élément `Location`. La commande `Restore` utilise alors la chaîne de connexion contenue dans la propriété `ConnectionString`. Si la propriété `ConnectionString` n'est pas spécifiée, la commande `Restore` utilise la chaîne de connexion stockée dans le fichier de sauvegarde pour la source de données distante spécifiée. Vous pouvez utiliser le paramètre `ConnectionString` pour déplacer une partition distante vers une autre instance distante. Toutefois, vous ne pouvez pas utiliser le paramètre `ConnectionString` pour restaurer une partition distante dans l'instance qui contient la base de données restaurée. En d'autres termes, vous ne pouvez pas utiliser la propriété `ConnectionString` pour transformer une partition distante en partition locale.  
  
-   Pour chaque dossier d’origine utilisé pour stocker les partitions distantes sur la source de données distante, vous pouvez spécifier un élément de [dossier](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/folder-element-xmla) pour indiquer le nouveau dossier dans lequel restaurer toutes les partitions distantes stockées dans le dossier d’origine. Si aucun élément `Folder` n'est spécifié, la commande `Restore` utilise les dossiers d'origine spécifiés pour les partitions distantes contenues dans le fichier de sauvegarde distant.  
  
### <a name="relocating-rolap-objects"></a>Déplacement d'objets ROLAP  
 La commande `Restore` ne peut pas restaurer les agrégations ou les données d'objets qui utilisent le stockage ROLAP, car ces informations sont stockées dans des tables de source de données relationnelle sous-jacente. Toutefois, les métadonnées d'objets ROLAP peuvent être restaurées. Pour restaurer les métadonnées d'un objet ROLAP, la commande `Restore` recrée la structure des tables d'une source de données relationnelle.  
  
 Vous pouvez utiliser l'élément `Location` dans une commande `Restore` pour déplacer des objets ROLAP. Pour chaque `Location` élément utilisé pour déplacer une source de données, la `DataSourceType` propriété doit être définie explicitement sur *local*. Vous devez également définir la chaîne de connexion du nouvel emplacement dans la propriété `ConnectionString` de l'élément `Location`. Au cours de la restauration, la commande `Restore` remplace la chaîne de connexion de la source de données identifiée par la propriété `DataSourceID` de l'élément `Location` par la valeur de la propriété `ConnectionString` de l'élément `Location`.  
  
##  <a name="synchronizing_databases"></a>Synchronisation des bases de données  
 La commande `Synchronize` permet de synchroniser les données et les métadonnées d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] spécifiée avec une autre base de données. La commande `Synchronize` possède plusieurs propriétés qui vous permettent de spécifier la base de données source, le mode de synchronisation des définitions de sécurité, les partitions distantes à synchroniser, ainsi que la synchronisation des objets ROLAP.  
  
> [!NOTE]  
>  La commande `Synchronize` ne peut être exécutée que par les administrateurs de serveur et les administrateurs de base de données. Les bases de données source et de destination doivent avoir le même niveau de compatibilité de base de données.  
  
### <a name="specifying-the-source-database"></a>Spécification de la base de données source  
 La propriété [source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) de la `Synchronize` commande contient deux propriétés, `ConnectionString` et `Object`. La propriété `ConnectionString` contient la chaîne de connexion de l'instance qui contient la base de données source, tandis que la propriété `Object` contient l'identificateur d'objet de la base de données source.  
  
 La base de données de destination est la base de données active de la session dans laquelle s'exécute la commande `Synchronize`.  
  
 Si la propriété `ApplyCompression` de la commande `Synchronize` est définie à true, les informations destinées à être envoyées de la base de données source vers la base de données de destination sont compressées avant d'être envoyées.  
  
### <a name="synchronizing-security-settings"></a>Synchronisation des paramètres de sécurité  
 La propriété [SynchronizeSecurity](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla) détermine si la `Synchronize` commande synchronise les définitions de sécurité, telles que les rôles et les autorisations, définies sur la base de données source. La propriété `SynchronizeSecurity` détermine également si la commande `Sychronize` inclut les comptes et groupes d'utilisateurs Windows définis comme membres des définitions de sécurité.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*SkipMembership*|Inclut les définitions de sécurité dans la base de données de destination mais exclut les informations d'appartenance.|  
|*CopyAll*|Inclut les définitions de sécurité et les informations d'appartenance dans la base de données de destination.|  
|*IgnoreSecurity*|Exclut les définitions de sécurité de la base de données de destination.|  
  
### <a name="synchronizing-remote-partitions"></a>Synchronisation de partitions distantes  
 Pour chaque source de données distante qui existe dans la base de données source, vous pouvez synchroniser chaque partition distante associée en incluant un élément `Location` dans la propriété `Locations` de la commande `Synchronize`. Pour chaque `Location` élément, la `DataSourceType` propriété doit être exclue ou explicitement définie sur *distant*.  
  
 Pour définir et se connecter à une source de données distante dans la base de données de destination, la commande `Synchronize` utilise la chaîne de connexion définie dans la propriété `ConnectionString` de l'élément `Location`. La commande `Synchronize` utilise alors la propriété `DataSourceID` de l'élément `Location` pour identifier les partitions distantes à synchroniser. La `Synchronize`commande synchronise les partitions distantes sur la source de données distante `DataSourceID` spécifiée dans la propriété de la base de données source avec la source `DataSourceID` de données distante spécifiée dans la propriété de la base de données de destination.  
  
 Pour chaque dossier d'origine utilisé pour stocker les partitions distantes de la source de données distante de la base de données source, vous pouvez également spécifier un élément `Folder` dans l'élément `Location`. L'élément `Folder` indique le nouveau dossier de la base de données de destination dans lequel seront synchronisées toutes les partitions distantes stockées dans le dossier d'origine de la source de données distante. Si aucun élément `Folder` n'est spécifié, la commande Synchronize utilise les dossiers d'origine spécifiés pour les partitions distantes contenues dans la base de données source.  
  
### <a name="synchronizing-rolap-objects"></a>Synchronisation d'objets ROLAP  
 La commande `Synchronize` ne peut pas synchroniser les agrégations ou les données d'objets qui utilisent le stockage ROLAP, car ces informations sont stockées dans des tables de source de données relationnelle sous-jacente. Toutefois, les métadonnées d'objets ROLAP peuvent être synchronisées. Pour synchroniser les métadonnées, la commande `Synchronize` recrée la structure des tables d'une source de données relationnelle.  
  
 Vous pouvez utiliser l'élément `Location` dans une commande Synchronize pour synchroniser des objets ROLAP. Pour chaque `Location` élément utilisé pour déplacer une source de données, la `DataSourceType` propriété doit être définie explicitement sur *local*. . Vous devez également définir la chaîne de connexion du nouvel emplacement dans la propriété `ConnectionString` de l'élément `Location`. Au cours de la synchronisation, la commande `Synchronize` remplace la chaîne de connexion de la source de données identifiée par la propriété `DataSourceID` de l'élément `Location` par la valeur de la propriété `ConnectionString` de l'élément `Location`.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Backup &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Élément Restore &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Synchroniser l’élément &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)   
 [Sauvegarde et restauration de bases de données Analysis Services](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
