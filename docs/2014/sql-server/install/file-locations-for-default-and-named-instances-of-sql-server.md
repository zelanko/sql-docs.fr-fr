---
title: Emplacements des fichiers pour les instances par défaut et les instances nommées de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 463c570e-9f75-4653-b3b8-4d61753b0013
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6363dd09dba21273e57b6b087002000bec4e54dc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012598"
---
# <a name="file-locations-for-default-and-named-instances-of-sql-server"></a>Emplacements des fichiers pour les instances par défaut et les instances nommées de SQL Server
  Une installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se compose d'une ou de plusieurs instances distinctes. Une instance, qu'elle soit par défaut ou nommée, possède son propre jeu de fichiers programmes et de fichiers de données, ainsi qu'un ensemble de fichiers communs partagés entre toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présentes sur l'ordinateur.  
  
 Pour une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui inclut [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], chaque composant a un jeu complet de fichiers de données et de fichiers exécutables, ainsi que des fichiers communs partagés par tous les composants.  
  
 Pour isoler l'emplacement d'installation de chaque composant, un ID d'instance unique est généré pour chaque composant d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]donnée.  
  
> [!IMPORTANT]  
>  Les fichiers programmes et les fichiers de données ne peuvent pas être installés sur un lecteur de disque amovible, dans un système de fichiers utilisant la compression, dans un répertoire où figurent des fichiers système ni sur des lecteurs partagés sur une instance de cluster de basculement.  
>   
>  Les bases de données système (master, model, MSDB, et tempdb) et les bases de données utilisateur du [!INCLUDE[ssDE](../../includes/ssde-md.md)] peuvent être installées avec le serveur de fichiers SMB (Server Message Block) comme option de stockage. Cela s'applique à la fois aux installations autonomes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et aux installations de cluster de basculement (FCI) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour en savoir plus, voir [Installer SQL Server avec le partage de fichiers SMB en tant qu'option de stockage](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
>   
>  Vous ne devez supprimer ni les répertoires suivants ni leur contenu : Binn, Data, Ftdata, HTML ou 1033. Si besoin est, vous pouvez supprimer d'autres répertoires mais il est possible que vous ne puissiez pas récupérer certaines fonctionnalités ou données sans désinstaller puis réinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ne supprimez pas et ne modifiez pas les fichiers .htm se trouvant dans le répertoire HTML. Ils sont nécessaires pour que les outils de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnent correctement.  
  
## <a name="shared-files-for-all-instances-of-ssnoversion"></a>Fichiers partagés pour toutes les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Les fichiers communs utilisés par toutes les instances sur un seul ordinateur sont installés dans le dossier [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)] , où \<*drive*> est la lettre du lecteur sur lequel les composants sont installés. La valeur par défaut est généralement le lecteur C.  
  
## <a name="file-locations-and-registry-mapping"></a>Emplacements des fichiers et mappage du Registre  
 Au cours de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un ID d'instance est généré pour chaque composant serveur. Les composants de cette version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 L'ID d'instance par défaut est construit à l'aide du format suivant :  
  
-   MSSQL pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)], suivi du numéro de version principale, puis d'un trait de soulignement et du numéro de version secondaire, le cas échéant, puis d'un point et du nom de l'instance.  
  
-   MSAS pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], suivi du numéro de version principale, puis d'un trait de soulignement et du numéro de version secondaire, le cas échéant, puis d'un point et du nom de l'instance.  
  
-   MSRS pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], suivi du numéro de version principale, puis d'un trait de soulignement et du numéro de version secondaire, le cas échéant, puis d'un point et du nom de l'instance.  
  
 Voici quelques exemples d'ID d'instance par défaut dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   MSSQL12.MSSQLSERVER pour une instance par défaut de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   MSAS12.MSSQLSERVER pour une instance par défaut de [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].  
  
-   MSSQL12.MyInstance pour une instance nommée de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] intitulée « MyInstance ».  
  
 La structure de répertoire pour une instance nommée de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] incluant le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], intitulée « MyInstance » et installée sur les répertoires par défaut, se présenterait de la façon suivante :  
  
-   C:\Program Files\Microsoft SQL Server\MSSQL12.MyInstance\  
  
-   C:\Program Files\Microsoft SQL Server\MSAS12.MyInstance\  
  
 Vous pouvez spécifier n'importe quelle valeur pour l'ID d'instance, mais évitez les caractères spéciaux et les mots clés réservés.  
  
 Vous pouvez spécifier un ID d'instance non défini par défaut pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Au lieu de \<Program Files> \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un \<custom path> \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est utilisé si l’utilisateur choisit de modifier le répertoire d’installation par défaut. Notez que les ID d'instance qui commencent avec un trait de soulignement (_) ou qui contiennent le signe dièse (#) ou le symbole dollar ($) ne sont pas pris en charge.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les composants clients ne sont pas dépendants d'une instance et, par conséquent, ne se voient pas attribuer d'ID d'instance. Par défaut, les composants ne dépendant pas d'une instance sont installés dans un répertoire unique : [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]. La modification du chemin d'installation d'un composant partagé affecte également les autres composants partagés. En effet, les installations ultérieures placent des composants ne prenant pas en charge les instances dans le même répertoire que celui prévu par l'installation d'origine.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]est le seul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composant qui prend en charge le changement de nom d’instance après l’installation. Si une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est renommée, l'ID d'instance ne change pas. Une fois l'attribution du nouveau nom de l'instance terminée, les répertoires et les clés de Registre continuent à utiliser l'ID d'instance créé pendant l'installation.  
  
 La ruche du Registre est créée sous HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*ID_instance*> pour les composants qui prennent en charge les instances. Par exemple,  
  
-   HKLM\Software \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. MyInstance  
  
-   HKLM\Software \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSAS12. MyInstance  
  
-   HKLM\Software \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSRS12. MyInstance  
  
 Le Registre maintient également le mappage d'un ID d'instance sur un nom d'instance. Le mappage de l'ID d'instance sur le nom d'instance se maintient comme suit :  
  
-   [HKEY_LOCAL_MACHINE \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \Software [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \Instance Names\SQL] "nom_instance" = "MSSQL12"  
  
-   [HKEY_LOCAL_MACHINE \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \Software [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \Instance Names\OLAP] "nom_instance" = "MSAS12"  
  
-   [HKEY_LOCAL_MACHINE \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \Software [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \Instance Names\RS] "nom_instance" = "MSRS12"  
  
## <a name="specifying-file-paths"></a>Spécification des chemins d'accès des fichiers  
 Pendant l'installation, vous pouvez modifier le chemin d'installation des fonctionnalités suivantes :  
  
 Ce chemin d'installation s'affiche uniquement dans le programme d'installation pour les fonctionnalités dotées d'un dossier de destination configurable par l'utilisateur.  
  
|Composant|Chemin d’accès par défaut<sup>1, 2</sup>|Chemin d’accès configurable<sup>3</sup> ou fixe|  
|---------------|---------------------------------|--------------------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] composants serveur|\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceID> \MSSQL12. \| Configurable|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] fichiers de données|\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceID> \MSSQL12. \| Configurable|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server|\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceID> \MSAS12. \| Configurable|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fichiers de données|\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceID> \MSAS12. \| Configurable|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] serveur de rapports|\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSRS12. \<InstanceID> \Reporting Services\ReportServer\Bin \| configurable|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Gestionnaire de rapports|\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSRS12. \<InstanceID> \|Chemin fixe \Reporting Services\ReportManager|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|\<Install Directory>\120\DTS \| configurable<sup>4</sup>|  
|Composants clients (sauf bcp.exe et sqlcmd.exe)|\<Install Directory>\120\Tools \| configurable<sup>4</sup>|  
|Composants clients (bcp.exe et sqlcmd.exe)|\<Install Directory>\Client SDK\ODBC\110\Tools\Binn|Chemin fixe|  
|Objets COM côté serveur et de réplication|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM \\ <sup>5</sup>|Chemin fixe|  
|DLL des composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour le moteur d'exécution de transformation des données, le moteur pipeline de transformation des données et l'utilitaire d'invite de commandes `dtexec`|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|Chemin fixe|  
|DLL qui assurent la prise en charge de connexions managées pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Connections|Chemin fixe|  
|DLL pour chaque type d'énumérateur que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend en charge|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\ForEachEnumerators|Chemin fixe|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fournisseurs WMI|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]\|Chemin d’accès fixe partagé|  
|Composants qui sont partagés entre toutes les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]\|Chemin d’accès fixe partagé|  
  
 <sup>1</sup> Assurez-vous que le dossier \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \ est protégé avec des autorisations limitées.  
  
 <sup>2</sup> Le lecteur par défaut de ces emplacements est *systemdrive*, normalement le lecteur C.  
  
 <sup>3</sup> Les chemins d’installation des fonctionnalités enfants sont déterminés par le chemin d’installation de la fonctionnalité parente.  
  
 <sup>4</sup> Un chemin d’installation unique est partagé entre [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les composants clients. La modification du chemin d'installation d'un composant affecte également les autres composants. En effet, les installations ultérieures placent les composants dans l'emplacement prévu par l'installation d'origine.  
  
 <sup>5</sup> Ce répertoire est utilisé par toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur. Si vous effectuez une mise à jour sur l'une des instances situées sur l'ordinateur, toute modification apportée aux fichiers de ce dossier affecte toutes les instances de l'ordinateur. Lors de l'ajout de fonctionnalités à une installation existante, vous ne pouvez ni modifier l'emplacement d'une fonctionnalité précédemment installée, ni spécifier l'emplacement d'une nouvelle fonctionnalité. Vous devez soit installer les fonctionnalités supplémentaires dans les répertoires déjà établis par le programme d'installation, soit désinstaller et réinstaller le produit.  
  
> [!NOTE]  
>  Pour les configurations en cluster, vous devez sélectionner un lecteur local disponible sur chaque nœud du cluster.  
  
 Lorsque, pendant l'installation, vous indiquez un chemin d'installation pour les composants serveur ou les fichiers de données, le programme d'installation utilise l'ID de l'instance, en plus de l'emplacement spécifié pour les fichiers programmes et les fichiers de données. Le programme d'installation n'utilise pas l'ID d'instance pour les outils et les autres fichiers partagés. S'il ne l'utilise pas non plus pour les fichiers programmes et les fichiers de données de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , il l'utilise en revanche pour le référentiel de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Si vous définissez le chemin d'installation de la fonctionnalité du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise ce chemin comme répertoire racine de tous les dossiers spécifiques à l'instance pour cette installation, y compris les fichiers de données SQL. Dans ce cas, si vous définissez la racine sur «C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. \<InstanceName> \MSSQL \\ ", les répertoires spécifiques à l’instance sont ajoutés à la fin de ce chemin.  
  
 Les clients qui choisissent d'utiliser la fonctionnalité de mise à niveau USESYSDB dans l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (mode d'interface utilisateur du programme d'installation) peuvent aisément se trouver dans une situation où le produit est installé dans une structure de dossiers récursive. Par exemple, \<*SQLProgramFiles*> \mssql12\mssql\ MSSQL10_50 \MSSQL\DATA \\ . Pour utiliser la fonctionnalité USESYSDB, il est donc conseillé de définir un chemin d'installation pour la fonctionnalité fichiers de données SQL au lieu de la fonctionnalité [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
> [!NOTE]
>  Les fichiers de données se situent généralement dans un répertoire enfant nommé « Data ». Par exemple, spécifiez C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. \<InstanceName> \ pour spécifier le chemin d’accès racine au répertoire de données des bases de données système pendant la mise à niveau lorsque les fichiers de données se trouvent sous C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. \<InstanceName> \MSSQL\Data.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de Moteur de base de données-répertoires de données](../../../2014/sql-server/install/database-engine-configuration-data-directories.md)   
 [Configuration de Analysis Services – Répertoires de données](../../../2014/sql-server/install/analysis-services-configuration-data-directories.md)  
  
  
