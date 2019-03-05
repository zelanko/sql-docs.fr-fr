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
ms.openlocfilehash: 9dba11c0130dc3b969a9fcec46b631abd7d62fe8
ms.sourcegitcommit: 2ab79765e51913f1df6410f0cd56bf2a13221f37
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2019
ms.locfileid: "56956050"
---
# <a name="list-of-bugs-fixed"></a>Liste des bogues corrigés

Cette page contient une liste des bogues corrigés dans chaque version, en commençant par [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17 du pilote ODBC pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.3 du pilote ODBC pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Fuite de mémoire TCP envoi notification événement handle fixe
- Problème de redéfinition fixe de _SQL_FILESTREAM_DESIRED_ACCESS enum dans le fichier d’en-tête msodbcsql.h
- AUTHENTIFICATION et jeton d’accès manquant fixe liés définition dans le fichier d’en-tête msodbcsql.h pour Linux

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.2 du pilote ODBC pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Correction d’un message d’erreur concernant l’authentification Azure Active Directory
- Correction de la détection encodage lorsque les variables d’environnement de paramètres régionaux sont définis différemment
- Fixe à un incident sur Déconnecter avec récupération de la connexion en cours
- Correction de la détection de l’activité de connexion
- Correction de la détection incorrecte de sockets fermés
- Correction d’une attente infinie lorsque vous tentez de libérer un descripteur d’instruction au cours de récupération ayant échoué
- Fixe le comportement de la désinstallation incorrecte lorsque les deux versions 13 et 17 sont installés sur Windows
- Comportement de déchiffrement fixe sur une plateforme plus ancienne de Windows (Windows 7, 8 et Server 2012)
- Correction d’un problème de cache lors de l’utilisation de l’authentification ADAL sur Windows
- Correction d’un problème qui a été de verrouillage et de remplacement trace ouvre une session sur Windows

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.1 de pilote ODBC pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Fixe le délai de 1 seconde lors de l’appel SQLFreeHandle lorsque MARS est activé et l’attribut de connexion « Encrypt = yes »
- Correction d’un incident de l’erreur 22003 dans SQLGetData lorsque la taille du tampon transmis dans est plus petite, les données extraites (Windows)
- Correction des messages d’erreur ADAL tronquée
- Correction d’un bogue rare sur 32 bits Windows lors de la conversion flottante point nombre en entier
- Correction d’un problème où insertion double dans un champ décimal avec Always Encrypted sur retournerait erreur de troncation de données
- Correction d’un avertissement sur le programme d’installation Mac OS
- Correction d’envoi état incorrect vers SQL Server lors de la tentative de récupération de la Session lors de la résilience des connexions et le regroupement de connexions à la fois sont activées, à l’origine de la session doit être supprimée par le serveur

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>Correctifs de bogues dans le [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17 du pilote ODBC pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Correction d’un bogue où lorsque vous utilisez l’authentification Kerberos, l’insertion en bloc peut échouer avec l’erreur « accès refusé »
- Solution de contournement supprimée pour un bogue unixODBC présent dans la version ci-dessous 2.3.1 (pilote a doublé les tailles de certaines mémoires tampon transmises à unixODBC)
- Correction de la résilience des connexions (reconnexion) en retrait lors de l’utilisation de ColumnEncryption = activé
- Correction bogue de la création de source de données, où lorsque le « Authentification Interactive Active Directory » option d’authentification Azure fenêtre peut devenir ne répond pas (Windows)
- Correction d’un incident rare lors de l’arrêt ODBC lors de l’exécution asynchrone est activée (s’est produite lors de la suppression de handle de connexion)
- Correction d’un problème où SQL pilote a entraîné une consommation du processeur élevée lors de l’exécution de procédures stockées long
- Élimination de l’incapacité pour récupérer des données dans une colonne varbinary (max) chiffrée sans conversion
- Résolution d’un problème où après un varchar (max) null colonne chiffrée est extraite à l’aide de SQLGetData() sur un curseur statique, la colonne suivante est également annulée même si elle comporte des données
- Correction d’un problème avec l’extraction de champs varbinary (max) avec Always Encrypted sur
- Correction d’un problème de setlocale() ne fonctionne ne pas avec Always Encrypted
- Correction d’un problème avec SQLDescribeParam() retour d’erreur lorsqu’elle est appelée sur le paramètre de procédure stockée de type XML avec Always Encrypted sur
- Fixes avec séquence d’échappement des traits de soulignement ne fonctionne ne pas dans SQLTables
- Correction d’un bogue où les données hébreu (varchar) sont tronquées lorsque retourné comme des caractères étendus sur Linux
- Correction d’un problème avec interrogation Shift-JIS encodé char/varchar à partir de l’application de UTF-8
- Correction du bogue où l’appelant SQLGetInfo avec le paramètre SQL_DRIVER_NAME retourné Linux-style de nom de fichier sur MacOS
- Correction d’un problème où le chargement des données de caractères Windows-1252, à l’aide d’entrée fichiers supérieur à 32k octets dans des colonnes VARCHAR à l’aide de l’utilitaire BCP entraînerait des échecs
