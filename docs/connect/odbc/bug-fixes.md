---
title: Liste des bogues corrigés | Microsoft Docs
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 9aba2495e5f4661c7c042125608f34d577cddfe3
ms.sourcegitcommit: e821cd8e5daf95721caa1e64c2815a4523227aa4
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702811"
---
# <a name="list-of-bugs-fixed"></a>Liste des bogues corrigés

Cette page contient la liste des bogues corrigés dans chaque version, [!INCLUDE[msCoName](../../includes/msconame_md.md)] à partir du pilote ODBC 17 pour[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-174-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] pilote ODBC 17,4 pour[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Correction du blocage intermittent lorsque MARS (Multiple Active Result Sets) est activé
- Corriger la résilience de la connexion se bloquer lorsque la notification asynchrone est activée
- Résolution d’un incident lors de la récupération des enregistrements de diagnostic pour les tentatives de connexion multithread
- Correction du chiffrement non pris en charge lors de la reconnexion après avoir appelé SQLGetInfo () avec SQL_USER_NAME et SQL_DATA_SOURCE_READ_ONLY
- Corriger l’erreur d’initialisation COM lors de l’Azure Active Directory de l’authentification interactive
- Corriger SQLGetData () pour les données UTF8 sur plusieurs octets
- Correction de la récupération de la longueur des colonnes sql_variant à l’aide de SQLGetData ()
- Correction de l’importation de colonnes sql_variant contenant plus de 7992 octets à l’aide de BCP
- Correction de l’envoi d’un encodage correct vers le serveur pour les données de caractères étroits

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] pilote ODBC 17,3 pour[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Fuite de mémoire du handle d’événement de notification d’envoi TCP fixe
- Correction du problème de redéfinition de l’énumération _SQL_FILESTREAM_DESIRED_ACCESS dans le fichier d’en-tête msodbcsql. h
- Correction du ACCESS_TOKEN manquant et de la définition de l’authentification dans le fichier d’en-tête msodbcsql. h pour Linux

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] pilote ODBC 17,2 pour[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Correction d’un message d’erreur concernant l’authentification Azure Active Directory
- Correction de la détection du codage lorsque les variables d’environnement de paramètres régionaux sont définies différemment
- Résolution d’un incident lors de la déconnexion avec récupération de la connexion en cours
- Correction de la détection de l’activité de la connexion
- Correction de détection incorrecte des sockets fermés
- Correction d’une attente infinie lors de la tentative de libération d’un descripteur d’instruction pendant une récupération ayant échoué
- Correction du comportement de désinstallation incorrect lors de l’installation des versions 13 et 17 sur Windows
- Correction du comportement de déchiffrement sur la plateforme Windows plus ancienne (Windows 7, 8 et Server 2012)
- Résolution d’un problème de cache lors de l’utilisation de l’authentification ADAL sur Windows
- Résolution d’un problème qui consistait à verrouiller et à remplacer les journaux de suivi sur Windows

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] pilote ODBC 17,1 pour[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Délai de 1 seconde fixe lors de l’appel de SQLFreeHandle avec MARS activé et attribut de connexion "Encrypt = Yes"
- Correction d’une erreur 22003 dans SQLGetData lorsque la taille de la mémoire tampon passée est inférieure aux données récupérées (Windows)
- Correction des messages d’erreur ADAL tronqués
- Correction d’un bogue rare sur Windows 32 bits lors de la conversion d’un nombre à virgule flottante en entier
- Correction d’un problème où l’insertion de double dans le champ décimal avec Always Encrypted sur retournerait une erreur de troncation de données
- Correction d’un avertissement dans le programme d’installation MacOS
- Correction de l’envoi d’un état incorrect à SQL Server lors de la tentative de récupération de session lorsque la résilience des connexions et le regroupement de connexions sont activés, ce qui provoque la suppression de la session par le serveur

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Correction d’un bogue à l’origine de l’utilisation de l’authentification Kerberos, l’insertion en bloc peut échouer avec l’erreur «Accès refusé»
- Suppression de la solution de contournement pour un bogue unixODBC présent dans la version ci-dessous (le pilote a doublé la taille de certaines mémoires tampons transmises à unixODBC)
- Résilience de connexion fixe (reconnexion) bloquée lors de l’utilisation de ColumnEncryption = Enabled
- Correction du bogue de création d’un DSN, où l’option «Active Directory l’authentification interactive» peut cesser de répondre (Windows)
- Correction d’un incident rare pendant l’arrêt de ODBC lorsque l’exécution asynchrone est activée (s’est produite lors de l’effacement du handle de connexion)
- Résolution d’un problème où le pilote SQL provoquait une consommation élevée du processeur lors de l’exécution de procédures stockées longues
- Correction de l’impossibilité de récupérer des données dans une colonne varbinary (max) chiffrée sans conversion
- Résolution d’un problème où après une colonne chiffrée de type varchar (max) null a été extraite à l’aide de SQLGetData () sur un curseur statique, la colonne suivante est également null, même si elle contient des données
- Correction d’un problème lors de l’extraction du champ varbinary (max) avec Always Encrypted sur
- Résolution d’un problème de setlocale () qui ne fonctionnait pas avec Always Encrypted
- Correction d’un problème avec SQLDescribeParam () retournant une erreur lorsqu’elle a été appelée sur un paramètre de procédure stockée de type XML avec Always Encrypted sur
- Traits de soulignement fixes placés dans une séquence d’échappement qui ne fonctionnent pas dans SQLTables
- Correction d’un bogue dans lequel les données hébraïques (varchar) sont tronquées lorsqu’elles sont renvoyées sous forme de caractères larges sur Linux
- Correction d’un problème lors de l’interrogation de char/varchar encodé par Shift-JIS à partir d’une application UTF-8
- Correction du bogue dans lequel l’appel de SQLGetInfo avec le paramètre SQL_DRIVER_NAME a retourné un nom de fichier de type Linux sur MacOS
- Résolution d’un problème où le chargement de données de caractères Windows-1252, l’utilisation de fichiers d’entrée de plus de 32 Ko dans des colonnes VARCHAR utilisant l’utilitaire BCP entraînerait des échecs
