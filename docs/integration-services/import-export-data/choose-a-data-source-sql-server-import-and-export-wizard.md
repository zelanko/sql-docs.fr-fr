---
title: "Choisir une source de donn&#233;es (Assistant Importation et Exportation SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.chooseadatasource.f1"
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 124
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 113
---
# Choisir une source de donn&#233;es (Assistant Importation et Exportation SQL Server)
  Après la page d’accueil, l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche **Choisir une source de données**. Dans cette page, vous indiquez la source de vos données et la façon de s’y connecter.
  
Pour plus d’informations sur les sources de données que vous pouvez utiliser, consultez [Quelles sont les sources et destinations de données que je peux utiliser ?](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>Capture d’écran de la page Choisir une source de données 
La capture d’écran suivante montre la première partie de la page **Choisir une source de données** de l’Assistant.

![Choisir la source](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>Choisir une source de données
 **Source de données**  
Spécifiez la source de données en sélectionnant le fournisseur de données qui peut se connecter à la source. Dans la plupart des cas, le fournisseur de données dont vous avez besoin est indiqué par son nom, car le nom du fournisseur contient le nom de la source. Par exemple, SQL Server, Oracle, des fichiers plats, Excel, et Access.

La liste des fournisseurs de données disponibles affichée dans la liste **Source de données** dépend des fournisseurs installés sur votre ordinateur. Elle varie également selon que vous exécutez l’Assistant 32 bits ou 64 bits.

Plusieurs fournisseurs peuvent être disponibles pour votre source de données. En général, vous pouvez sélectionner n’importe quel fournisseur qui fonctionne avec votre source. Par exemple, pour vous connecter à Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, le fournisseur .NET Framework pour SQL Server ou le fournisseur Microsoft OLE DB pour SQL Server. 

Dans certains cas, vous devez commencer par sélectionner un fournisseur de données générique. Par exemple, si vous avez un pilote ODBC pour votre source de données, sélectionnez le fournisseur de données .NET Framework pour ODBC.  
 
Pour certaines sources de données, vous devrez peut-être télécharger le fournisseur de données à partir de Microsoft ou d’un tiers. Pour plus d’informations sur les sources de données que vous pouvez utiliser, consultez [Quelles sont les sources et destinations de données que je peux utiliser ?](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardSources)

## <a name="after-you-choose-a-data-source"></a>Une fois que vous avez choisi une source de données
Une fois que vous avez choisi une source de données, le reste de la propriété de la page **Choisir une source de données** a un nombre variable d’options qui dépendent du fournisseur de données choisi.

Les sections suivantes répertorient les options importantes pour certaines sources de données fréquemment utilisées. Toutes les sources disponibles dans la liste déroulante **Source de données** ne sont pas répertoriées ici. Pour obtenir des options supplémentaires et d’autres fournisseurs, consultez la documentation spécifique au fournisseur. 
  
> [!TIP]  Si votre source de données nécessite une chaîne de connexion, des exemples sont disponibles sur ce site tiers : [The Connection Strings Reference](https://www.connectionstrings.com/).  

## <a name="microsoft-sql-server"></a>Microsoft SQL Server 

### <a name="connect-to-sql-server-with-sql-server-native-client-or-the-microsoft-ole-db-provider-for-sql-server"></a>Se connecter à SQL Server avec SQL Server Native Client ou le fournisseur Microsoft OLE DB pour SQL Server  

SQL Server Native Client et le fournisseur Microsoft OLE DB pour SQL Server proposent le même ensemble d’options. La capture d’écran suivante montre les options de SQL Server Native Client à titre d’exemple.

![Connexion SQL Server Native Client](../../integration-services/import-export-data/media/sql-server-connection-native.png)

 **Nom du serveur**  
 Tapez le nom ou l’adresse IP du serveur qui contient les données, ou choisissez un serveur dans la liste.  
  
> [!NOTE] Si vous êtes sur un réseau doté de plusieurs serveurs, il peut être plus facile à taper le nom du serveur. Si vous cliquez sur la liste déroulante, l’interrogation du réseau pour connaître tous les serveurs disponibles peut prendre beaucoup de temps, et le nom de votre serveur peut ne pas figurer dans les résultats.

Pour indiquer un port TCP non standard, tapez une virgule après l’adresse IP ou le nom du serveur, puis tapez le numéro de port.
  
 **Utiliser l’authentification Windows**  
 Spécifiez si l’Assistant doit utiliser l’authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows pour la connexion à la base de données. L'authentification Windows est recommandée pour renforcer la sécurité.  
  
 **Utiliser l’authentification SQL Server**  
 Spécifiez si l’Assistant doit utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion à la base de données. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d’utilisateur**  
 Fournissez un nom d’utilisateur pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Base de données**  
 Sélectionnez dans la liste la base de données pour l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiée.  
  
 **Actualiser**  
 Cliquez sur **Actualiser** pour actualiser la liste des bases de données disponibles.  
  
### <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>Se connecter à SQL Server avec le fournisseur de données .NET Framework pour SQL Server 

Cette page présente une liste groupée des options pour le fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les options importantes sont répertoriées ici. Les options supplémentaires fournies quand vous sélectionnez ce fournisseur ne sont généralement pas indispensables pour la connexion à la base de données source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 

Pour plus d’informations, consultez [.NET Framework Data Provider for SQL Server connection strings](https://www.connectionstrings.com/sqlconnection/).

![Fournisseur de données .NET Framework pour SQL Server](../../integration-services/import-export-data/media/sql-server-connection-net.png)
  
 **Source de données**  
 Tapez le nom ou l’adresse IP du serveur qui contient les données, ou choisissez un serveur dans la liste.  
  
> [!NOTE] Si vous êtes sur un réseau doté de plusieurs serveurs, il peut être plus facile à taper le nom du serveur. Si vous cliquez sur la liste déroulante, l’interrogation du réseau pour connaître tous les serveurs disponibles peut prendre beaucoup de temps, et le nom de votre serveur peut ne pas figurer dans les résultats.  
 
 Pour indiquer un port TCP non standard, tapez une virgule après l’adresse IP ou le nom du serveur, puis tapez le numéro de port.
 
 **Catalogue initial**  
 Tapez le nom de la base de données source ou choisissez une base de données dans la liste.  
  
 **Sécurité intégrée**  
 Spécifiez **True** pour établir la connexion en utilisant l’authentification intégrée de Windows (recommandé) ou **False** pour établir la connexion en utilisant l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous spécifiez **False**, vous devez entrer un ID d'utilisateur et un mot de passe. La valeur par défaut est **False**.  
  
 **ID d’utilisateur**  
 Fournissez un nom d’utilisateur pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="oracle"></a>Oracle

Connectez-vous à Oracle à l’aide du fournisseur de données .NET Framework pour Oracle ou le fournisseur Microsoft OLE DB pour Oracle. Le fournisseur de données .NET Framework pour Oracle, illustré dans la capture d’écran suivante, est plus facile à configurer.

Pour plus d’informations, consultez [.NET Framework Data Provider for Oracle connection strings](https://www.connectionstrings.com/net-framework-data-provider-for-oracle/) ou [Microsoft OLE DB Provider for Oracle connection strings](https://www.connectionstrings.com/microsoft-ole-db-provider-for-oracle-msdaora/).

![Connexion Oracle](../../integration-services/import-export-data/media/oracle-connection.png)

## <a name="odbc-data-sources"></a>sources de données ODBC

Pour charger des données à partir d’une source qui fournit un pilote ODBC, sélectionnez le fournisseur de données .NET Framework pour ODBC.

Pour fournir une chaîne de connexion à une source de données ODBC, consultez la documentation du pilote ODBC que vous voulez utiliser, ou recherchez des exemples ici : [The Connection Strings Reference](https://www.connectionstrings.com/). 

La capture d’écran suivante montre une connexion ODBC à SQL Server à titre d’exemple. La chaîne de connexion utilisée dans l’exemple est la suivante :

    Driver={SQL Server};Server=(local);Database=TestData;Trusted_Connection=Yes;

Une fois que vous avez entré la chaîne de connexion dans le champ **ConnectionString**, l’Assistant analyse la chaîne et affiche les propriétés individuelles et leurs valeurs dans la section **Divers** de la liste.

![Connexion ODBC à SQL Server](../../integration-services/import-export-data/media/odbc-connection-sql.png)

## <a name="text-files-flat-files"></a>Fichiers texte (fichiers plats)
 
 Si vous utilisez des fichiers plats comme sources de données, plusieurs pages d’options vous sont proposées.
 
 ### <a name="general-page"></a>Page Général
 Dans la page **Général**, accédez au fichier, puis vérifiez les paramètres de la section **Format**.
 
 ![Page Général de la connexion à un fichier plat](../../integration-services/import-export-data/media/flat-file-connection-general.png)  
   
Pour plus d’informations sur la page **Général**, consultez la page [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md) dans les informations de référence sur Integration Services.  

### <a name="columns-page"></a>Page Colonnes

 Dans la page **Colonnes**, vérifiez la liste des colonnes et les délimiteurs identifiés par l’Assistant.
 
 ![Colonnes utilisées pour la connexion à un fichier plat](../../integration-services/import-export-data/media/flat-file-connection-columns.png)
  
Pour plus d’informations sur la page **Colonnes**, consultez la page [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md) dans les informations de référence sur Integration Services.

### <a name="advanced-page"></a>Page Avancé

La page **Avancé** affiche des informations détaillées sur chaque colonne de la source de données, notamment son type de données et sa taille.

Dans la capture d’écran suivante, vous pouvez constater que les données de la colonne **id** sont initialement de type chaîne.

![Page Avancé de la connexion à un fichier plat (avant)](../../integration-services/import-export-data/media/flat-file-connection-advanced-before.png)

Cliquez sur **Suggérer les types** pour afficher la boîte de dialogue **Suggérer les types de colonnes**. 

![Suggérer les types de colonnes dans le cadre de la connexion à un fichier plat](../../integration-services/import-export-data/media/flat-file-connection-suggest.png)

Une fois que vous avez choisi des options dans la boîte de dialogue **Suggérer les types de colonnes**, cliquez sur **OK**. L’Assistant peut alors modifier les types de données de certaines colonnes à importer.

Dans la capture d’écran suivante, l’Assistant reconnaît que la colonne **id** de la source de données est en fait un nombre et non une chaîne de texte. Il remplace alors le type chaîne des données de la colonne par le type entier.

![Page Avancé de la connexion à un fichier plat (après)](../../integration-services/import-export-data/media/flat-file-connection-advanced-after.png)
  
Pour plus d’informations sur la page **Avancé**, consultez la page [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md) dans les informations de référence sur Integration Services.

### <a name="preview-page"></a>Page Aperçu

Dans la page **Aperçu**, vérifiez que la liste des colonnes et que les exemples de données sont conformes à vos attentes.

![Page Aperçu de la connexion à un fichier plat](../../integration-services/import-export-data/media/flat-file-connection-preview.png)

Pour plus d’informations sur la page **Aperçu**, consultez la page [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md) dans les informations de référence sur Integration Services.  
 
## <a name="microsoft-excel"></a>Microsoft Excel

La capture d’écran suivante montre un exemple de connexion à un classeur Microsoft Excel.

![Connexion à Excel](../../integration-services/import-export-data/media/excel-connection.png) 
 
 **Chemin du fichier Excel**  
 Spécifiez le chemin d'accès et le nom de la feuille de calcul à partir de laquelle les données doivent être importées. Par exemple, **C:\\MyData.xlsx** pour un fichier sur l’ordinateur local ou **\\\\Sales\\Database\\Northwind.xlsx** pour un fichier sur un partage réseau. Ou cliquez sur **Parcourir**.  
  
 **Parcourir**  
 Permet de rechercher la feuille de calcul à l’aide de la boîte de dialogue **Ouvrir**.  

> [!NOTE] L’Assistant ne peut pas ouvrir un fichier Excel protégé par mot de passe.

 **Version Excel**  
 Permet de sélectionner la version d’Excel utilisée par le classeur source.

Vous devrez peut-être télécharger et installer des fichiers supplémentaires pour vous connecter à la version d’Excel que vous sélectionnez. Consultez [Obtenir les téléchargements dont vous avez besoin pour Excel et Access](Choose%20a%20Data%20Source%20\%28SQL%20Server%20Import%20and%20Export%20Wizard%29.md\#officeDownloads) dans cette page pour plus d’informations.

Si vous rencontrez un problème quand vous spécifiez une version (par exemple, si vous ne pouvez pas installer le runtime Access 2016 parce que vous avez Microsoft Office 365), essayez de spécifier une autre version, même une version antérieure comme 2013 au lieu de 2016.

**La première ligne contient des noms de colonnes**  
Indiquez si la première ligne de données sources contient des noms de colonne.
-   Si les données sources ne contiennent pas de nom de colonne, mais que vous activez cette option, l’Assistant traite la première ligne de données sources comme les noms de colonne.
-   Si les données sources contiennent des noms de colonne, mais que vous désactivez cette option, l’Assistant traite la ligne de noms de colonne comme la première ligne de données.

Si les données sources n’ont pas de noms de colonne, l’Assistant utilise F1, F2 et ainsi de suite en interne comme titres de colonne temporaires.

## <a name="microsoft-access"></a>Microsoft Access  

La capture d’écran suivante montre un exemple de connexion à une base de données Microsoft Access.

![Connexion à Access](../../integration-services/import-export-data/media/access-connection.png)

 **Nom de fichier**  
 Spécifiez le chemin d'accès et le nom du fichier de base de données à partir duquel les données doivent être importées. Par exemple, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**. Ou cliquez sur **Parcourir**.
 
 >   [!NOTE] L’Assistant peut uniquement se connecter à une base de données Access au format de fichier .MDB.  
  
 **Parcourir**  
 Permet de rechercher le fichier de la base de données à l’aide de la boîte de dialogue **Ouvrir**.  
  
 **Nom d’utilisateur**  
Quand un fichier d’informations d’un groupe de travail est associé à la base de données, fournissez un nom d’utilisateur valide pour la connexion à la base de données.  
  
 **Mot de passe**  
Quand un fichier d’informations d’un groupe de travail est associé à la base de données, fournissez le mot de passe de l’utilisateur pour la connexion à la base de données.
 
Si la base de données est protégée par un seul mot de passe pour tous les utilisateurs, indiquez cette valeur dans la boîte de dialogue **Propriétés des liaisons de données**. Pour ouvrir la boîte de dialogue **Propriétés des liaisons de données**, cliquez sur **Avancé**.  
  
 **Avancé**  
Permet de spécifier les options avancées, telles que le mot de passe de la base de données ou un autre fichier d’informations de groupe de travail que celui défini par défaut, à l’aide de la boîte de dialogue **Propriétés des liaisons de données**.  
  
## <a name="a-nameofficedownloadsaget-the-downloads-you-need-for-excel-and-access"></a><a name="officeDownloads"></a>Obtenir les téléchargements dont vous avez besoin pour Excel et Access  
Vous devrez peut-être télécharger les composants de connectivité pour les sources de données Microsoft Excel et Access s’ils ne sont pas déjà installés.

Les versions ultérieures des composants peuvent ouvrir des fichiers créés par les versions antérieures des programmes. Dans certains cas, les versions antérieures des composants peuvent également ouvrir des fichiers créés par les versions ultérieures des programmes.  
  
Si l’ordinateur a une version 32 bits d’Office, vous devez installer la version 32 bits des composants. Vous devez également vérifier que vous exécutez l’Assistant (ou le package Integration Services qu’il crée) en mode 32 bits.  
|Version de Microsoft Office|Télécharger|  
|------------------------------|--------------|  
|2007|[Pilote Office System 2007 : composants de connectivité de données](https://www.microsoft.com/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|  
 
 
## <a name="azure-blob-storage"></a>Stockage d'objets blob d'Azure  
Pour utiliser Azure Blob Source, vous devez installer Azure Feature Pack pour SSIS. Pour plus d’informations, consultez [Feature Pack Azure pour Integration Services &#40;SSIS&#41;](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  

>   [!NOTE] Pour que le Gestionnaire de connexions Azure Storage et les composants qui l’utilisent, notamment la source d’objets blob, puissent se connecter à la fois aux comptes de stockage à usage général et aux comptes de stockage d’objets blob, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). Pour plus d’informations sur ces deux types de comptes de stockage, consultez [Introduction à Microsoft Azure Storage](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts).

![Connexion à Azure Blob Storage](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

 **Utiliser un compte Azure**  
 Indiquez si vous souhaitez utiliser un compte en ligne.
  
 **Nom du compte de stockage**  
 Spécifiez le nom du compte de stockage Azure.  
  
**Clé de compte**  
Spécifiez la clé du compte de stockage Azure.  
  
 **Utiliser HTTPS**  
 Indiquez si vous souhaitez vous connecter au compte de stockage avec HTTP ou HTTPS.  
  
 **Utiliser un compte de développeur local**  
 Spécifiez s’il convient d’utiliser l’émulateur de stockage sur l’ordinateur local.  
  
 **Nom du conteneur d’objets blob**  
 Sélectionnez un nom dans la liste des conteneurs de stockage disponibles dans le compte de stockage spécifié.  
  
 **Format du fichier d’objets blob**  
 Sélectionnez le format de fichier Texte ou Avro.  
  
 **Délimiteur de colonne**  
 Si vous avez sélectionné le format Texte, spécifiez le caractère délimiteur de colonne.  
  
 **Utiliser la première ligne comme noms de colonne**  
 Spécifiez si la première ligne de données contient des noms de colonne.  
  
## <a name="whats-next"></a>Étape suivante  
 Une fois que vous avez fourni les informations relatives à la source de vos données et indiqué comment s’y connecter, la page **Choisir une destination** s’affiche. Dans cette page, vous fournissez les informations relatives à la destination de vos données et à la façon de s’y connecter. Pour plus d’informations, consultez [Choisir une destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).  
