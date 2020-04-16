---
title: Créer une application
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e65eaac59bcc16e123bda3e47af29dc4a836ce5
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388399"
---
# <a name="creating-a-driver-application"></a>Création d’une application de pilote
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  L'architecture ODBC possède quatre composants qui effectuent les fonctions ci-dessous.  
  
|Composant|Fonction|  
|---------------|--------------|  
|Application|Appelle les fonctions ODBC pour communiquer avec une source de données ODBC, soumet les instructions SQL et traite les jeux de résultats.|  
|Gestionnaire de pilote|Gère la communication entre une application et tous les pilotes ODBC utilisés par cette application.|  
|Pilote|Traite tous les appels des fonctions ODBC à partir de l'application, se connecte à une source de données, passe les instructions SQL de l'application à la source de données et retourne les résultats à l'application. Si nécessaire, le pilote traduit des données ODBC SQL de l'application en données SQL natif utilisées par la source de données.|  
|Source de données|Contient toutes les informations dont un pilote a besoin pour accéder à une instance spécifique des données dans un SGBD.|  
  
 Une application qui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le conducteur native De l’ODBC pour communiquer avec une instance d’exécution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des tâches suivantes:  
  
-   Elle se connecte à une source de données.  
  
-   Elle envoie les instructions SQL à la source de données.  
  
-   Elle traite les résultats des instructions provenant de la source de données.  
  
-   Elle traite les erreurs et les messages.  
  
-   Elle met un terme à la connexion à la source de données.  
  
 Une application plus complexe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] écrite pour le conducteur de Native Client ODBC peut également effectuer les tâches suivantes :  
  
-   Utiliser des curseurs pour contrôler l'emplacement dans un jeu de résultats  
  
-   Demander des opérations de validation ou de restauration pour le contrôle des transactions  
  
-   Effectuer des transactions distribuées qui impliquent deux serveurs ou plus  
  
-   Exécuter des procédures stockées sur le serveur distant  
  
-   Appeler des fonctions de catalogue pour obtenir des informations sur les attributs d'un jeu de résultats  
  
-   Effectuer des opérations de copie en bloc  
  
-   Gérer les grandes données **(varchar(max)**, les colonnes **nvarchar(max)** et **varbinaires (max)**  
  
-   Utiliser la logique de reconnexion pour faciliter le basculement lorsque la mise en miroir de bases de données est configurée  
  
-   Enregistrer des données de performances et des requêtes longues  
  
 Pour effectuer des appels de fonction ODBC, une application C ou C++ doit inclure les fichiers d'en-tête sql.h, sqlext.h et sqltypes.h. Pour effectuer des appels aux fonctions API du programme d'installation ODBC, une application doit inclure le fichier d'en-tête odbcinst.h. Une application ODBC Unicode doit inclure le fichier d'en-tête sqlucode.h. Les applications ODBC doivent être liées au fichier odbc32.lib. Les applications ODBC qui appellent les fonctions API du programme d'installation ODBC doivent être liées au fichier odbccp32.lib. Ces fichiers sont inclus dans le Kit de développement Platform SDK de Windows.  
  
 De nombreux conducteurs de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’ODBC, y compris le chauffeur native ODBC, offrent des extensions ODBC spécifiques au conducteur. Pour profiter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des extensions spécifiques au conducteur native Client ODBC, une application doit inclure le fichier d’en-tête sqlncli.h. Ce fichier d'en-tête contient :  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Attributs de connexion spécifiques au conducteur de client autochtone ODBC.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC attributs de déclaration spécifique au conducteur.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC attributs colonne spécifique au conducteur.  
  
-   Les types de données spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Les types de données définis par l'utilisateur spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC conducteur spécifique [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) types.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC pilotes de diagnostic des pilotes champs.  
  
-   Les codes de fonction dynamique de diagnostic spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Les définitions de type C/C++ pour les types de données C natifs spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (retournées lorsque les colonnes ont créé une liaison avec le type de données C SQL_C_BINARY).  
  
-   Tapez la définition pour la structure de données SQLPERF.  
  
-   Copiez en bloc les macros et les prototypes pour prendre en charge l'utilisation d'API de copie en bloc par le biais d'une connexion ODBC.  
  
-   Appelez les fonctions API de métadonnées de requête distribuée pour obtenir les listes des serveurs liés et leurs catalogues.  
  
 Toute application C ou CMD ODBC qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la fonction de copie en vrac du conducteur native ODBC doit être liée au fichier sqlncli11.lib. Les applications qui appellent les fonctions API de métadonnées de requête distribuée doivent également être liées à sqlncli11.lib. Les fichiers sqlncli.h et sqlncli11.lib sont [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distribués dans le cadre des outils du développeur. Les répertoires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include et Lib doivent correspondre aux chemins d'accès INCLUDE et LIB du compilateur, comme suit :  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 Une décision de conception à prendre tôt dans le processus de génération d'une application est de savoir si l'application doit avoir plusieurs appels ODBC en attente en même temps. Il existe deux méthodes de prise en charge des appels ODBC concurrents multiples ; elles sont décrites dans les autres rubriques de cette section. Pour plus d’informations, consultez la [référence du programmeur de l’ODBC](https://go.microsoft.com/fwlink/?LinkId=45250).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mode asynchrone et SQLCancel](../../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md)  
  
-   [Applications multithread](../../../relational-databases/native-client/odbc/creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
