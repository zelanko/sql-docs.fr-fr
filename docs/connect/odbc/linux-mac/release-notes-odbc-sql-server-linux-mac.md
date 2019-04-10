---
title: Notes de publication d’ODBC sur Linux et macOS | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: MightyPen
ms.technology: connectivity
ms.topic: conceptual
author: karinazhou
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 6f6cdc23073585f5a9a6a8cee0c3fc779f7ca27a
ms.sourcegitcommit: 3cfedfeba377560d460ca3e42af1e18824988c07
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59042896"
---
# <a name="release-notes-for-the-microsoft-odbc-driver-to-sql-server-on-linux-and-macos"></a>Notes de publication de Microsoft ODBC Driver for SQL Server sur Linux et macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article liste et décrit les nouveautés des publications versionnées du pilote ODBC [!INCLUDE[msCoName](../../../includes/msconame_md.md)] pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS.

<!--
Going forward, please use the new 2-column markdown table for each new H2 version section.
And we are keeping the H2 titles much shorter, partly by removing redundant or obvious info.
We want to track the Month YYYY each new version H2 section is added, at the end of the H2 title.
This is the new standard format for Release Notes article content.

OLD     FILE NAME:    linux-mac/release-notes.md
NOW NEW FILE NAME:    linux-mac/release-notes-odbc-sql-server-linux-mac.md

Thank you.
GeneMi.  2019/04/03.
-->

## <a name="173-february-2019"></a>17.3, février 2019

| Nouvel élément | Détails |
| :------- | :------ |
| Nouvelles distributions prises en charge. | &bull; &nbsp; &nbsp; SuSE 15<br/>&bull; &nbsp; &nbsp; Ubuntu 18.10<br/>&bull; &nbsp; &nbsp; macOS 10.14 |
| Mode d’authentification Azure Active Directory Managed Service Identity (avec attribution par le système et l’utilisateur) | Consultez [Utilisation d’Azure Active Directory avec ODBC Driver](../using-azure-active-directory.md). |
| Possibilité d’envoyer des paramètres d’entrée sur les colonnes Always Encrypted. | Pour plus d’informations, consultez [Limitations du pilote ODBC lors de l’utilisation d’Always Encrypted](../using-always-encrypted-with-the-odbc-driver.md#limitations-of-the-odbc-driver-when-using-always-encrypted). |
| Transactions distribuées XA. | Consultez [Utilisation de transactions XA](../use-xa-with-dtc.md).<br/><br/>XA est le sigle d’_eXtended Architecture_, standard pour l’exécution d’une transaction globale qui accède à plusieurs systèmes de stockage de données côté serveur. |
| &nbsp; | &nbsp; |

## <a name="172-july-2018"></a>17.2, juillet 2018

| Nouvel élément | Détails |
| :------- | :------ |
| Nouvelles distributions prises en charge. | &bull; &nbsp; &nbsp; Ubuntu 18.04 |
| Classification des données pour Azure SQL Database et SQL Server. | Consultez [Classification des données](../data-classification.md). |
| Prise en charge de l’encodage serveur UTF-8. | &nbsp; |
| `SQLBrowseConnect` | &nbsp; |
| Dépendance dynamique sur `libcurl`. | À partir de cette version, le package `libcurl` n’est pas une dépendance explicite.<br/>Le package `libcurl` pour OpenSSL ou NSS est requis lors de l’utilisation de l’authentification Azure Key Vault ou Azure Active Directory.<br/>Si vous rencontrez une erreur concernant `libcurl`, vérifiez qu’il est installé. |
| Résilience des connexions inactives avec les mots clés ConnectRetryCount et ConnectRetryInterval dans la chaîne de connexion. | &bull; &nbsp; &nbsp; Utilisez `SQL_COPT_SS_CONNECT_RETRY_COUNT`(lecture seule) pour récupérer le nombre de nouvelles tentatives de connexion.<br/><br/>&bull; &nbsp; &nbsp; Utilisez `SQL_COPT_SS_CONNECT_RETRY_INTERVAL`(lecture seule) pour récupérer la longueur de l’intervalle des nouvelles tentatives de connexion.<br/><br/>Consultez [Résilience de connexion du pilote ODBC Windows](../windows/connection-resiliency-in-the-windows-odbc-driver.md). |
| Correctifs de bogues. | [Correctifs de bogues](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="171-march-2018"></a>17.1, mars 2018

| Nouvel élément | Détails |
| :------- | :------ |
| Prise en charge des attributs de connexion `SQL_COPT_SS_CEKCACHETTL` et `SQL_COPT_SS_TRUSTEDCMKPATHS`. | &bull; &nbsp; &nbsp; `SQL_COPT_SS_CEKCACHETTL` permet de contrôler la durée d’existence du cache local des clés de chiffrement de colonne, ainsi que son vidage.<br/><br/>&bull; &nbsp; &nbsp; `SQL_COPT_SS_TRUSTEDCMKPATHS` permet à l’application de limiter les opérations Always Encrypted à la seule utilisation de la liste spécifiée de clés principales de colonne.<br/><br/>Consultez [Utilisation d’Always Encrypted avec ODBC Driver for SQL Server](../using-always-encrypted-with-the-odbc-driver.md). |
| Prise en charge du chargement du `.rll` à partir de l’emplacement par défaut. | Consultez la [section « Chargement du fichier de ressources » dans le document Installation](installing-the-microsoft-odbc-driver-for-sql-server.md#resource-file-loading). |
| Correctifs de bogues. | [Correctifs de bogues](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="17"></a>17

**Nouvelles distributions prises en charge** : macOS High Sierra et Ubuntu 17.10 

**Optimisation des performances** : les performances sont plus que décuplées quand le pilote convertit vers/depuis UTF-8/16.

**Fonctionnalités ajoutées** :

Prise en charge d’Always Encrypted pour l’API BCP

Le nouvel attribut de chaîne de connexion UseFMTOnly conduit le pilote à utiliser les métadonnées héritées dans les cas spéciaux nécessitant des tables temporaires.

Prise en charge d’Azure SQL Managed Instance (préversion privée étendue). 
> [!NOTE]
> Il existe plusieurs différences lors de l’utilisation de Managed Instance :
> -   FILESTREAM n’est pas pris en charge. 
> -   L’accès au système de fichiers local n’est pas pris en charge, mais est nécessaire pour certaines choses telles que les fichiers de trace 
> -   La création d’un UDT depuis le chemin local n’est pas prise en charge 
> -   L’authentification intégrée de Windows n’est pas prise en charge 
> -   DTC n’est pas pris en charge 
> -   Le compte « sa » n’est pas présent (le compte par défaut est appelé « cloudSA »).
> -   L’erreur de jeton TDS (0xAA) retourne un nom de serveur incorrect
> -   Les caractères spéciaux dans les noms de base de données ne sont pas pris en charge 
> -   ALTER DATABASE [nom_bd_1] MODIFY NAME = [nom_bd_2] n’est pas pris en charge
> -   Les messages d’erreur sont toujours affichés en anglais, quels que soient les paramètres de langue (à l’image d’Azure) 

## <a name="131-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos-may-2017"></a>13.1, pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS, mai 2017

ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ajoute la prise en charge d’Always Encrypted et d’Azure Active Directory quand il est utilisé conjointement avec Microsoft SQL Server 2016.

**Nouvelles distributions prises en charge** : OS X 10.11 et macOS 10.12 sont pris en charge dans la première version du pilote ODBC sur macOS. Ubuntu 16.10 est maintenant également pris en charge ainsi que Red Hat 6, 7 et SUSE 12. Chaque plateforme dispose d’un package relatif à la plateforme (RPM ou DEB) pour faciliter l’installation et la configuration.  Consultez [Installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) pour obtenir des instructions d’installation.

**Modifications apportées à la prise en charge d’unixODBC Driver Manager 2.3.1** : le pilote ODBC ne dépend plus d’un empaquetage personnalisé pour le gestionnaire de pilotes unixODBC (sauf sur RedHat 6) et, à la place, s’appuie sur le gestionnaire de package de distribution pour résoudre la dépendance UnixODBC à partir des dépôts de la distribution.

**Prise en charge de l’API BCP** : le pilote ODBC Linux et macOS prend désormais en charge l’utilisation des [fonctions de l’API BCP (**bcp_init**, etc.)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="130-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>13.0, pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux

Avec Microsoft ODBC Driver 13.0 for SQL Server, SQL Server 2014 et SQL Server 2016 sont désormais également pris en charge.  

**Nouvelles distributions prises en charge.**  :

Ubuntu est maintenant pris en charge, ainsi que Red Hat et SUSE. Chaque plateforme dispose d’un package relatif à la plateforme (RPM ou DEB) pour faciliter l’installation et la configuration.  Consultez [Installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) pour obtenir des instructions d’installation.

**Prise en charge d’unixODBC Driver Manager 2.3.1** : outre un nouveau gestionnaire de pilotes, il existe un package pour l’installation de cette dépendance qui facilite l’installation et la configuration.  

**Résolution d’adresses IP réseau transparente** : « Résolution d’adresses IP réseau transparente » est une révision de la fonctionnalité « Basculement de plusieurs sous-réseaux » existante qui affecte la séquence de connexion du pilote si la première adresse IP résolue du nom d’hôte ne répond pas et que plusieurs adresses IP sont associées au nom d’hôte.

**Prise en charge de TLS 1.2** : Microsoft ODBC Driver 13.0 for SQL Server sur Linux prend désormais en charge TLS 1.2 quand des communications sécurisées avec SQL Server sont utilisées.

## <a name="11-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>11, pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux

Le pilote ODBC sur SUSE Linux (Preview) prend en charge 64 bits SUSE Linux Enterprise 11 Service Pack 2. Pour plus d’informations, consultez [System Requirements](../../../connect/odbc/linux-mac/system-requirements.md).  

Le pilote ODBC sur Linux prend en charge les [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Pour plus d’informations, consultez [Prise en charge par le pilote ODBC pour Linux de la haute disponibilité et de la reprise d’activité](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  

Le pilote ODBC sur Linux prend en charge les connexions à Microsoft Azure SQL Database. Pour plus d’informations, consultez [How to: Connect to Windows Azure SQL Database Using ODBC](https://msdn.microsoft.com/library/hh974312.aspx).  

L’option `-l` (délai d’expiration de la connexion) a été ajoutée à `bcp`. Pour plus d’informations, consultez [Connexion avec **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).
