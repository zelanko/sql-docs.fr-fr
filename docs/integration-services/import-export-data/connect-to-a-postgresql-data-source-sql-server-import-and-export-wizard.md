---
title: "Se connecter à une Source de données de PostgreSQL (SQL Server Assistant Importation et exportation) | Documents Microsoft"
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
ms.assetid: b7a75a72-b267-444f-9eb8-d23eb333fc35
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4c82ae7eedc3e18e7591cf7ab30a507920695247
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données de PostgreSQL (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **PostgreSQL** de source de données à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation. 

> [!IMPORTANT]
> Les exigences détaillées et les conditions préalables requises pour la connexion à une base de données PostgreSQL n’entrent pas dans le cadre de cet article de Microsoft. Cet article suppose que vous avez déjà PostgreSQL logiciel client est installé et que vous pouvez déjà se connecter à la base de données PostgreSQL. Pour plus d’informations, consultez votre administrateur de base de données PostgreSQL ou la documentation PostgreSQL.

## <a name="get-the-postgresql-odbc-driver"></a>Obtenir le pilote ODBC de PostgreSQL

### <a name="install-the-odbc-driver-with-stack-builder"></a>Installer le pilote ODBC avec le Générateur de pile
Exécuter le Générateur de pile pour ajouter le pilote PostgreSQL ODBC (psqlODBC) à votre installation de PostgreSQL.

![Installer PostgreSQL ODBC avec le Générateur de pile](../../integration-services/import-export-data/media/install-postgresql-odbc-with-stack-builder.png)

### <a name="or-download-the-latest-odbc-driver"></a>Ou téléchargez le dernier pilote ODBC
Télécharger le programme d’installation de Windows pour la dernière version du pilote ODBC de PostgreSQL (psqlODBC) directement à partir de ce site FTP - [https://www.postgresql.org/ftp/odbc/versions/msi/](https://www.postgresql.org/ftp/odbc/versions/msi/). Extrayez les fichiers à partir du fichier .zip et exécutez le fichier .msi.

## <a name="connect-to-postgresql-with-the-postgresql-odbc-driver-psqlodbc"></a>Se connecter à PostgreSQL avec le pilote PostgreSQL ODBC (psqlODBC)
Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des sources de données. Pour vous connecter avec un pilote ODBC, commencez par sélectionner le **fournisseur de données .NET Framework pour ODBC** comme source de données sur le **choisir une Source de données** ou **choisir une Destination** page. Ce fournisseur agit comme un wrapper autour du pilote ODBC.

Voici l’écran générique que vous voyez immédiatement après avoir sélectionné le fournisseur de données .NET Framework pour ODBC.

![Se connecter à PostgreSQL avec ODBC avant](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-postgresql-odbc-driver"></a>Options pour spécifier (pilote PostgreSQL ODBC)

> [!NOTE]
> Les options de connexion pour ce fournisseur de données et le pilote ODBC sont les mêmes si PostgreSQL est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

Pour vous connecter à PostgreSQL avec le pilote ODBC de PostgreSQL, assembler une chaîne de connexion qui inclut les paramètres suivants et leurs valeurs. Le format de chaîne de connexion complète immédiatement après la liste des paramètres.

> [!TIP]
> Obtenir de l’aide d’assembler une chaîne de connexion est bonne. Ou, au lieu de fournir une chaîne de connexion, fournir une source de données existante (nom de source de données) ou créez-en un. Pour plus d’informations sur ces options, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Pilote**  
Le nom du pilote ODBC - soit **PostgreSQL ODBC Driver(UNICODE)** ou **PostgreSQL ODBC Driver(ANSI)**.

**Server**  
Le nom du serveur PostgreSQL. 

**Port**  
Le port à utiliser pour se connecter au serveur PostgreSQL.

**Base de données**  
Le nom de la base de données PostgreSQL.

**UID** et **Pwd**   
Le **Uid** (id utilisateur) et **Pwd** (mot de passe) pour vous connecter.

### <a name="connection-string-format"></a>Format de chaîne de connexion
Voici le format d’une chaîne de connexion par défaut. 

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=<server>;Port=<port>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>Entrez la chaîne de connexion
Entrez la chaîne de connexion dans le **ConnectionString** champ, ou entrez le nom de source de données dans le **Dsn** champ sur la **choisir une Source de données** ou **choisir une Destination** page. Après avoir entré la chaîne de connexion, l’Assistant analyse la chaîne et affiche les propriétés et leurs valeurs dans la liste.

L’exemple suivant utilise cette chaîne de connexion.

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=127.0.0.1;Port=5432;Database=postgres;UID=postgres;PWD=********
    ```

Voici l’écran que vous voyez après avoir entré la chaîne de connexion.

![Se connecter à PostgreSQL avec ODBC](../../integration-services/import-export-data/media/connect-to-postgresql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Plus d’informations et les autres fournisseurs de données
Pour plus d’informations sur la façon de se connecter à PostgreSQL avec un fournisseur de données qui n’est pas répertorié ici, consultez [les chaînes de connexion PostgreSQL](https://www.connectionstrings.com/postgresql/). Ce site tiers contient également plus d’informations sur les fournisseurs de données et les paramètres de connexion décrites dans cette page.

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


