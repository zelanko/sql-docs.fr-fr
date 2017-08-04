---
title: "Se connecter à une Source de données SQL Server (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 386cedbb-fae5-45ce-9363-c4a417f80a2f
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 17910c8e30dee98f39e977896fb67774b54a798d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données SQL Server (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **Microsoft SQL Server** de source de données à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation. Il existe plusieurs fournisseurs de données que vous pouvez utiliser pour se connecter à SQL Server.

> [!TIP]
> Si vous êtes sur un réseau avec plusieurs serveurs, il peut être plus facile à entrer le nom du serveur au lieu de développer la liste déroulante des serveurs. Si vous cliquez sur la liste déroulante, il peut prendre beaucoup de temps pour interroger le réseau pour tous les serveurs disponibles, et les résultats ne peuvent pas inclure même le serveur souhaité.

## <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>Se connecter à SQL Server avec le fournisseur de données .NET Framework pour SQL Server 
Après avoir sélectionné **fournisseur de données .NET Framework pour SQL Server** sur la **choisir une Source de données** ou **choisir une Destination** page de l’Assistant, la page affiche une liste groupée des options pour le fournisseur. Bon nombre d'entre elles sont des noms hostiles et les paramètres inhabituels. Heureusement, pour vous connecter à une base de données d’entreprise, vous devez généralement fournir uniquement quelques informations. Vous pouvez ignorer les valeurs par défaut pour les autres paramètres.

> [!NOTE]
> Les options de connexion pour ce fournisseur de données sont les mêmes si SQL Server est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

|Informations nécessaires|.NET framework Data Provider pour la propriété de SQL Server|
|---|---|
|Nom du serveur|**Source de données**|
|Informations d’authentification (connexion)|**La sécurité intégrée de**; ou, **ID utilisateur** et **mot de passe**<br/>Si vous souhaitez afficher la liste déroulante des bases de données sur le serveur, vous devez d’abord fournir les informations de connexion valide.|
|Nom de la base de données|**Catalogue initial**|

![Se connecter à SQL avec le fournisseur .NET](../../integration-services/import-export-data/media/connect-to-sql-with-net-provider.jpg)

### <a name="options-to-specify-net-framework-data-provider-for-sql-server"></a>Options pour spécifier (fournisseur de données .NET Framework pour SQL Server)

> [!NOTE]
> Les options de connexion pour ce fournisseur de données sont les mêmes si SQL Server est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

**Source de données**  
 Entrez le nom ou l’adresse IP du serveur source ou de destination, ou sélectionnez un serveur dans la liste déroulante.  
 
 Pour spécifier un port TCP non standard, entrez une virgule après le nom du serveur ou l’adresse IP, puis entrez le numéro de port.
 
 **Catalogue initial**  
 Entrez le nom de la base de données source ou de destination, ou sélectionnez une base de données à partir de la liste déroulante.  
  
 **Sécurité intégrée**  
 Spécifiez **True** pour se connecter avec l’authentification intégrée de Windows (recommandée), ou **False** pour se connecter avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. Si vous spécifiez **False**, vous devez entrer un ID d'utilisateur et un mot de passe. La valeur par défaut est **False**.  
  
 **ID d'utilisateur**  
 Entrez un nom d’utilisateur si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.  
  
 **Mot de passe**  
 Entrez le mot de passe si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.  

## <a name="connect-to-sql-server-with-the-odbc-driver-for-sql-server"></a>Se connecter à SQL Server avec le pilote ODBC pour SQL Server 
Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des sources de données. Pour vous connecter avec un pilote ODBC, commencez par sélectionner le **fournisseur de données .NET Framework pour ODBC** comme source de données. Ce fournisseur agit comme un wrapper autour du pilote ODBC.

> [!TIP]
> **Obtenir le dernier pilote**. Téléchargez le [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).

Voici l’écran générique que vous voyez immédiatement après avoir sélectionné le fournisseur de données .NET Framework pour ODBC.

![Se connecter à SQL avec ODBC avant](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-sql-server"></a>Options pour spécifier (le pilote ODBC pour SQL Server)

> [!NOTE]
> Les options de connexion pour le pilote ODBC sont les mêmes si SQL Server est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

Pour vous connecter à SQL Server avec le dernier pilote ODBC, assembler une chaîne de connexion qui inclut les paramètres suivants et leurs valeurs. Le format de chaîne de connexion complète immédiatement après la liste des paramètres.

> [!TIP]
> Obtenir de l’aide d’assembler une chaîne de connexion est bonne. Ou, au lieu de fournir une chaîne de connexion, fournir une source de données existante (nom de source de données) ou créez-en un. Pour plus d’informations sur ces options, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Pilote**  
Le nom du pilote ODBC. Le nom est différent pour les différentes versions du pilote.

**Server**  
Le nom du serveur SQL.

**Base de données**  
Nom de la base de données.  

**Trusted_Connection**; ou, **Uid** et **Pwd**  
Spécifiez **Trusted_Connection = Yes** pour se connecter avec l’authentification intégrée Windows ; ou, spécifier **Uid** (id utilisateur) et **Pwd** (mot de passe) pour se connecter avec l’authentification SQL Server.

### <a name="connection-string-format"></a>Format de chaîne de connexion
Voici le format de chaîne de connexion qui utilise l’authentification intégrée de Windows.

    Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;trusted_connection=Yes;

Voici le format de chaîne de connexion qui utilise l’authentification SQL Server au lieu de l’authentification intégrée Windows.

     Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;uid=<user id>;pwd=<password>;

### <a name="enter-the-connection-string"></a>Entrez la chaîne de connexion
Entrez la chaîne de connexion dans le **ConnectionString** champ, ou entrez le nom de source de données dans le **Dsn** champ sur la **choisir une Source de données** ou **choisir une Destination** page. Après avoir entré la chaîne de connexion, l’Assistant analyse la chaîne et affiche les propriétés et leurs valeurs dans la liste.

L’exemple suivant utilise cette chaîne de connexion.

    Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;

Voici l’écran que vous voyez après avoir entré la chaîne de connexion.

![Se connecter à SQL avec ODBC après](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="connect-to-sql-server-with-the-microsoft-ole-db-provider-for-sql-server-or-sql-server-native-client"></a>Se connecter à SQL Server avec le fournisseur Microsoft OLE DB pour SQL Server ou SQL Server Native Client

> [!IMPORTANT]
> Le fournisseur Microsoft OLE DB pour SQL Server et SQL Server Native Client ne sont pas pris en charge dans les versions de SQL Server après SQL Server 2012. Utilisez le pilote ODBC à la place. Pour plus d’informations sur la transition vers le pilote ODBC, consultez les billets de blog suivants.
>   -   [Microsoft s’aligne sur ODBC pour l’accès aux données relationnel natif](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)
>   -   [Présentation les nouveaux pilotes ODBC de Microsoft SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/)

## <a name="other-data-providers-and-more-info"></a>Plus d’informations et les autres fournisseurs de données
Pour plus d’informations sur la façon de se connecter à SQL Server avec un fournisseur de données qui n’est pas répertorié ici, consultez [les chaînes de connexion SQL Server](https://www.connectionstrings.com/sql-server/). Ce site tiers contient également plus d’informations sur les fournisseurs de données et les paramètres de connexion décrites dans cette page.

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


