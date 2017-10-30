---
title: "Se connecter à une Source de données MySQL (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d7c5a38-18d3-4cc9-a241-04422cb250d3
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3df56fcda5b39c2895de83feac4f302686b1adf3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-mysql-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données MySQL (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **MySQL** de source de données à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation. Il existe plusieurs fournisseurs de données que vous pouvez utiliser pour se connecter à MySQL.

> [!IMPORTANT]
> Les exigences détaillées et les conditions préalables requises pour la connexion à une base de données MySQL n’entrent pas dans le cadre de cet article de Microsoft. Cet article suppose que vous avez déjà installé par le logiciel MySQL client et que vous pouvez déjà se connecter à la base de données MySQL. Pour plus d’informations, consultez votre administrateur de base de données MySQL ou la documentation MySQL.

## <a name="get-the-mysql-connectors"></a>Obtient les connecteurs MySQL
Télécharger les fournisseurs et pilotes décrites dans cette rubrique à partir de la [MySQL connecteurs](https://dev.mysql.com/downloads/connector/) page.

## <a name="connect-to-mysql-with-the-net-framework-data-provider-for-mysql"></a>Se connecter à MySQL avec .net Framework Data Provider pour MySQL
Après avoir sélectionné **fournisseur de données .NET Framework pour MySQL** sur la **choisir une Source de données** ou **choisir une Destination** page de l’Assistant, la page présente une liste groupée des options pour le fournisseur. Bon nombre d'entre elles sont des noms hostiles et les paramètres inhabituels. Heureusement, vous devez uniquement fournir quelques informations. Vous pouvez ignorer les valeurs par défaut pour les autres paramètres.

> [!NOTE]
> Les options de connexion pour ce fournisseur de données sont les mêmes si MySQL est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

|Informations nécessaires|.NET framework Data Provider pour la propriété de MySQL|
|---|---|
|Nom du serveur|**Server**|
|Nom de la base de données|**Base de données**|
|Informations d’authentification (connexion)|**Id d’utilisateur** et **mot de passe**|

Vous n’êtes pas obligé d’entrer la chaîne de connexion dans le **ConnectionString** champ de la liste. Une fois que vous entrez des valeurs individuelles pour le nom du serveur MySQL (**Server**) et les informations de connexion, l’Assistant assemble la chaîne de connexion à partir de chacune de ces propriétés et leurs valeurs. 

![Se connecter à MySQL avec le fournisseur .NET, 1 sur 2](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-1-of-2.png)

![Se connecter à MySQL avec le fournisseur .NET, 2 sur 2](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-2-of-2.png)

## <a name="connect-to-mysql-with-the-mysql-odbc-driver"></a>Se connecter à MySQL avec le pilote ODBC de MySQL
Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des sources de données. Pour vous connecter avec un pilote ODBC, commencez par sélectionner le **fournisseur de données .NET Framework pour ODBC** comme source de données sur le **choisir une Source de données** ou **choisir une Destination** page. Ce fournisseur agit comme un wrapper autour du pilote ODBC.

Voici l’écran générique que vous voyez immédiatement après avoir sélectionné le fournisseur de données .NET Framework pour ODBC.

![Se connecter à SQL avec ODBC avant](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-mysql-odbc-driver"></a>Options pour spécifier (le pilote ODBC MySQL)

> [!NOTE]
> Les options de connexion pour ce fournisseur de données et le pilote ODBC sont les mêmes si MySQL est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

Pour vous connecter à MySQL avec le pilote ODBC de MySQL, assembler une chaîne de connexion qui inclut les paramètres suivants et leurs valeurs. Le format de chaîne de connexion complète immédiatement après la liste des paramètres.

> [!TIP]
> Obtenir de l’aide d’assembler une chaîne de connexion est bonne. Ou, au lieu de fournir une chaîne de connexion, fournir une source de données existante (nom de source de données) ou créez-en un. Pour plus d’informations sur ces options, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Pilote**  
Le nom du pilote ODBC.

**Server**  
Le nom du serveur MySQL. 

**Base de données**  
Le nom de la base de données MySQL.

**UID** et **PWD**   
L’id utilisateur et un mot de passe pour se connecter.

### <a name="connection-string-format"></a>Format de chaîne de connexion
Voici le format d’une chaîne de connexion par défaut.

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=<server>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>Entrez la chaîne de connexion
Entrez la chaîne de connexion dans le **ConnectionString** champ, ou entrez le nom de source de données dans le **Dsn** champ sur la **choisir une Source de données** ou **choisir une Destination** page. Après avoir entré la chaîne de connexion, l’Assistant analyse la chaîne et affiche les propriétés et leurs valeurs dans la liste.

L’exemple suivant utilise cette chaîne de connexion.

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=127.0.0.1;Database=world;UID=root;PWD=********
    ```

Voici l’écran que vous voyez après avoir entré la chaîne de connexion.

![Se connecter à MySQL avec ODBC](../../integration-services/import-export-data/media/connect-to-mysql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Plus d’informations et les autres fournisseurs de données
Pour plus d’informations sur la façon de se connecter à MySQL avec un fournisseur de données qui n’est pas répertorié ici, consultez [les chaînes de connexion MySQL](https://www.connectionstrings.com/mysql/). Ce site tiers contient également plus d’informations sur les fournisseurs de données et les paramètres de connexion décrites dans cette page.

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


