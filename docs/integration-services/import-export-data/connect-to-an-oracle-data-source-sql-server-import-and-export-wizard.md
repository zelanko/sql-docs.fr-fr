---
title: "Se connecter à une Source de données Oracle (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0bd1f5a-34dd-4be3-9ac8-f9f87727781b
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e589e7f7a0262d258342bf887ec84c57d57dc978
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-oracle-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données Oracle (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **Oracle** de source de données à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation. Il existe plusieurs fournisseurs de données que vous pouvez utiliser pour se connecter à Oracle.

> [!IMPORTANT]
> Les exigences détaillées et les conditions préalables requises pour la connexion à une base de données Oracle n’entrent pas dans le cadre de cet article de Microsoft. Cet article suppose que vous avez déjà le logiciel client Oracle installé et que vous pouvez déjà se connecter à la base de données Oracle. Pour plus d’informations, consultez votre administrateur de base de données Oracle ou la documentation Oracle.

## <a name="connect-to-oracle-with-the-net-framework-data-provider-for-oracle"></a>Connexion à Oracle avec le .net Framework Data Provider pour Oracle
Après avoir sélectionné **fournisseur de données .NET Framework pour Oracle** sur la **choisir une Source de données** ou **choisir une Destination** page de l’Assistant, la page présente une liste groupée des options pour le fournisseur. Bon nombre d'entre elles sont des noms hostiles et les paramètres inhabituels. Heureusement, vous devez uniquement fournir deux ou trois éléments d’information. Vous pouvez ignorer les valeurs par défaut pour les autres paramètres.

> [!NOTE]
> Les options de connexion pour ce fournisseur de données sont les mêmes si Oracle est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

|Informations nécessaires|.NET framework Data Provider pour la propriété d’Oracle|
|---|---|
|Nom du serveur|**Source de données**|
|Informations d’authentification (connexion)|**ID d’utilisateur** et **mot de passe**; ou, **la sécurité intégrée**|

Vous n’êtes pas obligé d’entrer la chaîne de connexion dans le **ConnectionString** champ de la liste. Une fois que vous entrez des valeurs individuelles pour le nom du serveur Oracle (**Source de données**) et les informations de connexion, l’Assistant assemble la chaîne de connexion à partir de chacune de ces propriétés et leurs valeurs. 

![Connexion à Oracle avec le fournisseur .NET](../../integration-services/import-export-data/media/connect-to-oracle-with-net-provider.jpg)

## <a name="connect-to-oracle-with-the-microsoft-odbc-driver-for-oracle"></a>Connexion à Oracle avec le pilote Microsoft ODBC pour Oracle
Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des sources de données. Pour vous connecter avec un pilote ODBC, commencez par sélectionner le **fournisseur de données .NET Framework pour ODBC** comme source de données sur le **choisir une Source de données** ou **choisir une Destination** page. Ce fournisseur agit comme un wrapper autour du pilote ODBC.

Voici l’écran générique que vous voyez immédiatement après avoir sélectionné le fournisseur de données .NET Framework pour ODBC.

![Connexion à Oracle avec ODBC avant](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-oracle"></a>Options pour spécifier (le pilote ODBC pour Oracle)

> [!NOTE]
> Les options de connexion pour ce fournisseur de données et le pilote ODBC sont les mêmes si Oracle est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

Pour vous connecter à Oracle avec le pilote ODBC pour Oracle, assembler une chaîne de connexion qui inclut les paramètres suivants et leurs valeurs. Le format de chaîne de connexion complète immédiatement après la liste des paramètres.

> [!TIP]
> Obtenir de l’aide d’assembler une chaîne de connexion est bonne. Ou, au lieu de fournir une chaîne de connexion, fournir une source de données existante (nom de source de données) ou créez-en un. Pour plus d’informations sur ces options, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Pilote**  
Le nom du pilote ODBC, **Microsoft ODBC pour Oracle**.

**Server**  
Le nom du serveur Oracle. 

**UID** et **Pwd**   
L’id utilisateur et un mot de passe pour se connecter.

### <a name="connection-string-format"></a>Format de chaîne de connexion
Voici le format d’une chaîne de connexion par défaut.

    ```
    Driver={Microsoft ODBC for Oracle};Server=myServerAddress;Uid=myUsername;Pwd=myPassword;
    ```

### <a name="enter-the-connection-string"></a>Entrez la chaîne de connexion
Entrez la chaîne de connexion dans le **ConnectionString** champ, ou entrez le nom de source de données dans le **Dsn** champ sur la **choisir une Source de données** ou **choisir une Destination** page. Après avoir entré la chaîne de connexion, l’Assistant analyse la chaîne et affiche les propriétés et leurs valeurs dans la liste.

Voici l’écran que vous voyez après avoir entré la chaîne de connexion.

![Connexion à Oracle avec ODBC](../../integration-services/import-export-data/media/connect-to-oracle-with-odbc.jpg)

## <a name="whats-my-oracle-server-name"></a>Quel est mon nom de serveur Oracle ?
Exécutez une des requêtes suivantes pour obtenir le nom de votre serveur Oracle.

`SELECT host_name FROM v$instance`

ou

`SELECT sys_context('USERENV','SERVER_HOST') FROM dual`

## <a name="other-data-providers-and-more-info"></a>Plus d’informations et les autres fournisseurs de données
Pour plus d’informations sur la connexion à Oracle avec un fournisseur de données qui n’est pas répertorié ici, consultez [les chaînes de connexion Oracle](https://www.connectionstrings.com/oracle/). Ce site tiers contient également plus d’informations sur les fournisseurs de données et les paramètres de connexion décrites dans cette page.

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


