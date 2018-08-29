---
title: Notes de publication - Microsoft ODBC Driver for SQL Server sur Linux et macOS | Microsoft Docs
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: a12475a1f759be12949d5642e5af865b10e4af99
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787042"
---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Notes de publication pour Microsoft ODBC Driver for SQL Server sur Linux et macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Nouveautés de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS

**Nouvelles distributions prises en charge**: Ubuntu 18.04

**Fonctionnalités ajoutées**:

Classification des données pour la base de données SQL Azure et SQL Server, pour plus d’informations consultez [Classification des données](../data-classification.md)

SQLBrowseConnect

Dépendance dynamique sur `libcurl`:
- À partir de cette version, le `libcurl` package n’est pas une dépendance explicite. Le `libcurl` le package pour OpenSSL ou NSS est requis lors de l’utilisation de l’authentification Azure Key Vault ou Azure Active Directory. Si vous rencontrez une erreur concernant `libcurl`, vérifiez qu’il est installé.

Inactivité de la résilience des connexions avec les mots clés ConnectRetryCount et ConnectRetryInterval dans la chaîne de connexion (pour plus d’informations, consultez [résilience des connexions dans le pilote ODBC de Windows](../windows/connection-resiliency-in-the-windows-odbc-driver.md)) :
- Utilisez `SQL_COPT_SS_CONNECT_RETRY_COUNT`(lecture seule) pour récupérer le nombre de nouvelles tentatives de connexion.
- Utilisez `SQL_COPT_SS_CONNECT_RETRY_INTERVAL`(lecture seule) pour récupérer la longueur de l’intervalle de nouvelle tentative de connexion.
- Nouvelle tentative une fois par défaut.


[Correctifs de bogues](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Nouveautés de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS

**Fonctionnalités ajoutées**:

Prise en charge de `SQL_COPT_SS_CEKCACHETTL` et `SQL_COPT_SS_TRUSTEDCMKPATHS` attributs de connexion (pour plus d’informations, consultez [à l’aide de Always Encrypted avec le pilote ODBC pour SQL Server](../using-always-encrypted-with-the-odbc-driver.md))
- `SQL_COPT_SS_CEKCACHETTL` Permet de contrôler l’heure à laquelle le cache local des clés de chiffrement de colonne existe, ainsi que le vidage il
- `SQL_COPT_SS_TRUSTEDCMKPATHS` Permet à l’application limiter les opérations AE pour utiliser uniquement la liste spécifiée de clés principales de colonne



Prise en charge pour le chargement du `.rll` à partir de l’emplacement par défaut (pour plus d’informations, consultez ['Chargement de fichier ressource' une section dans le document Installation](installing-the-microsoft-odbc-driver-for-sql-server.md#resource-file-loading))

[Correctifs de bogues](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Nouveautés de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS

**Nouvelles distributions prises en charge**: macOS High Sierra et Ubuntu 17.10 

**Améliorations des performances**: supérieur à 10 x amélioration des performances lorsque le pilote convertit vers/à partir de UTF-8/16.

**Fonctionnalités ajoutées**:

Always Encrypted prise en charge des API BCP

Nouvel attribut de chaîne de connexion UseFMTOnly conduit le pilote à utiliser les métadonnées héritées dans les cas spéciaux nécessitant des tables temporaires.

Prise en charge pour Azure SQL Managed Instance (préversion privée étendue). 
> [!NOTE]
> Il existe plusieurs différences lors de l’utilisation de Managed Instance :
> -   FILESTREAM n’est pas pris en charge. 
> -   Accès de système de fichiers local n’est pas pris en charge, mais requis pour les opérations que tracefiles 
> -   Créer un type UDT depuis le système local chemin d’accès n’est pas pris en charge. 
> -   L’authentification intégrée de Windows n’est pas pris en charge. 
> -   DTC n’est pas pris en charge 
> -   compte 'sa' n’est pas présent (compte par défaut est appelé « cloudSA »)
> -   Erreur de jeton TDS (0xAA) retourne le nom de serveur incorrect
> -   Caractères spéciaux dans le nom de la base de données ne sont pas pris en charge. 
> -   ALTER DATABASE [dbname1] MODIFY NAME = [dbname2] n’est pas pris en charge.
> -   Les messages d’erreur sont toujours affichées en anglais, quelle que soit la langue des paramètres (identique à Azure) 

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Nouveautés de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS  

ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ajoute la prise en charge pour Always Encrypted et Azure Active Directory lorsqu’il est utilisé conjointement avec Microsoft SQL Server 2016.

**Nouvelles distributions prises en charge**: OS X 10.11 et macOS 10.12 sont pris en charge dans la première version du pilote ODBC sur macOS. Ubuntu 16.10 est maintenant également pris en charge, ainsi que Red Hat 6, 7 et SUSE 12. Chaque plateforme dispose d’un package relatifs à la plateforme (RPM ou DEB) pour faciliter l’installation et la configuration.  Consultez [l’installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) pour obtenir des instructions d’installation.

**unixODBC 2.3.1 du Gestionnaire de pilotes prise en charge des modifications**: le pilote ODBC ne dépend plus empaquetage personnalisé pour le Gestionnaire de pilotes unixODBC (sauf sur Red Hat 6) et à la place s’appuie sur le Gestionnaire de package de distribution pour résoudre la dépendance UnixODBC à partir de référentiels de la distribution.

**Prise en charge des API BCP**: Linux et macOS pilote ODBC prend désormais en charge l’utilisation de la [fonctions de l’API BCP (**bcp_init**, etc..)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Quelles sont les nouveautés dans Microsoft ODBC Driver 13.0 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux  
Avec Microsoft ODBC Driver 13.0 for SQL Server, SQL Server 2014 et SQL Server 2016 sont maintenant également pris en charge.  

**Nouvelles distributions prises en charge**:

Ubuntu est maintenant pris en charge, ainsi que Red Hat et SUSE. Chaque plateforme dispose d’un package relatifs à la plateforme (RPM ou DEB) pour faciliter l’installation et la configuration.  Consultez [l’installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) pour obtenir des instructions d’installation.

**unixODBC prise en charge du Gestionnaire de pilotes 2.3.1**: en plus d’un gestionnaire de pilotes plus récente, il existe également un package d’installation de cette dépendance qui facilite l’installation et la configuration.  

**Résolution d’adresses IP réseau transparente**: résolution d’adresses IP réseau Transparent est une révision de la fonctionnalité de basculement de sous-réseaux multiples existante qui affecte la séquence de connexion du pilote dans le cas où le premier résolu n’est pas le cas de l’adresse IP du nom d’hôte répondre et il y a plusieurs adresses IP associée avec le nom d’hôte.

**Prise en charge de TLS 1.2**: The Microsoft ODBC Driver 13.0 for SQL Server sur Linux prend désormais en charge TLS 1.2 lorsque sécuriser les communications avec SQL Server sont utilisées.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Nouveautés de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux  
Le pilote ODBC sur SUSE Linux (Preview) prend en charge 64 bits SUSE Linux Enterprise 11 Service Pack 2. Pour plus d’informations, consultez [Configuration système requise](../../../connect/odbc/linux-mac/system-requirements.md).  

Le pilote ODBC sur Linux prend en charge les [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Pour plus d’informations, consultez [pilote ODBC sur la prise en charge de Linux pour la haute disponibilité, récupération d’urgence](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  

Le pilote ODBC sur Linux prend en charge les connexions à Microsoft Azure SQL Database. Pour plus d’informations, consultez [How to: Connect to Windows Azure SQL Database Using ODBC](http://msdn.microsoft.com/library/hh974312.aspx).  

Le `-l` option (délai d’expiration de connexion) a été ajoutée à `bcp`. Pour plus d’informations, consultez [Connexion avec **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).
