---
title: Notes de publication d’ODBC pour SQL Server sur Windows | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
ms.reviewer: v-jizho2, v-chojas, genemi
author: v-makouz
ms.author: v-makouz
manager: kenvh
ms.openlocfilehash: d6eebce61ede6e1e3dd76028a653a00ffa06990e
ms.sourcegitcommit: e821cd8e5daf95721caa1e64c2815a4523227aa4
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702755"
---
# <a name="release-notes-for-odbc-to-sql-server-on-windows"></a>Notes de publication d’ODBC pour SQL Server sur Windows

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article de notes de publication décrit les nouveautés du pilote Microsoft ODBC pour SQL Server sur Windows.

<!--
PLEASE USE THE STANDARD 2-COLUMN TABLE FORMAT!

For all our Release Notes articles (What's New too?), we are standardizing on the 2-column format that you see here for version "## 17.3".

Going forward, all new additions to this article must use the 2-column format.

Also, use the shorter ## H2 title format, which eliminates all the redundant constants, and appends the date-added.
One beneift of shortness is the avoidance of the annoying wrapping of unnecessarily long H2 titles in the rightNav.
- OLD H2:  ## What's New in the [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Windows
- NEW H2:  ## 17.3, February 2019

By the way, in GitHub, the file name is changing today 2019/03/30:
- FROM:  docs/connect/odbc/windows/release-notes.md
- TO  :  docs/connect/odbc/windows/release-notes-odbc-sql-server-windows.md

Thank you.
GeneMi (and CraigG).  2019/03/30.
-->

## <a name="174-july-2019"></a>17.4, juillet 2019

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Always Encrypted avec les enclaves sécurisées. | Voir [Utilisation d’Always Encrypted avec ODBC Driver](../using-always-encrypted-with-the-odbc-driver.md). |
| Paramètres TCP Keep Alive configurables. | Voir [Connexion à SQL Server](../linux-mac/connection-string-keywords-and-data-source-names-dsns.md). |
| Correctifs de bogues. | Consultez [Correctifs de bogues](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="173-february-2019"></a>17.3, février 2019

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Mode d’authentification Azure Active Directory Managed Service Identity (avec attribution par le système et l’utilisateur) | Consultez [Utilisation d’Azure Active Directory avec ODBC Driver](../using-azure-active-directory.md). |
| Possibilité d’envoyer des paramètres d’entrée sur les colonnes Always Encrypted. | Consultez [Limitations du pilote ODBC lors de l’utilisation d’Always Encrypted](../using-always-encrypted-with-the-odbc-driver.md#limitations-of-the-odbc-driver-when-using-always-encrypted). |
| Transactions distribuées XA. | [Utilisation de transactions XA](../use-xa-with-dtc.md). |
| Correctifs de bogues. | Consultez [Correctifs de bogues](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="172-july-2018"></a>17.2, juillet 2018

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Classification des données pour Azure SQL Database et SQL Server. | Consultez [Classification des données](../data-classification.md). |
| Prise en charge de l’encodage serveur UTF-8. | &nbsp; |
| Correctifs de bogues. | Consultez [Correctifs de bogues](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="171-march-2018"></a>17.1, mars 2018

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge des attributs de connexion `SQL_COPT_SS_CEKCACHETTL` et `SQL_COPT_SS_TRUSTEDCMKPATHS`. | &bull; &nbsp; `SQL_COPT_SS_CEKCACHETTL`)<br/>Permet de contrôler la durée d’existence du cache local des clés de chiffrement de colonne, ainsi que son vidage.<br/><br/>&bull; &nbsp; `SQL_COPT_SS_TRUSTEDCMKPATHS`)<br/>Permet à l’application de limiter les opérations AE à la seule utilisation de la liste spécifiée de clés principales de colonne.<br/><br/> Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec ODBC Driver for SQL Server](../using-always-encrypted-with-the-odbc-driver.md). |
| Prise en charge de l’authentification interactive Azure Active Directory | &nbsp; |
| Correctifs de bogues. | Consultez [Correctifs de bogues](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="17-february-2018"></a>17, février 2018

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge d’Always Encrypted pour l’API BCP. | &nbsp; |
| Nouvel attribut de chaîne de connexion `UseFMTOnly`. | Oblige le pilote à utiliser les métadonnées héritées dans les cas spéciaux qui nécessitent des tables temporaires. |
| Prise en charge d’Azure SQL Managed Instance. | Préversion privée étendue.<br/><br/>Consultez la liste suivante de [différences lors de l’utilisation de Managed Instance (ODBC version 17)](#diffs-managed-instance-17). |
| &nbsp; | &nbsp; |

| Dépendance modifiée | Détails |
| :------------ | :------ |
| Suppression de l’Assistant de connexion aux services en ligne Microsoft | La dépendance a été supprimée. |
| &nbsp; | &nbsp; |

### <a name="diffs-managed-instance-17"></a> Différences lors de l’utilisation de Managed Instance (ODBC version 17)

Cette version d’ODBC prend en charge Azure SQL Managed Instance (préversion privée étendue). Consultez la liste suivante de différences lors de l’utilisation de Managed Instance.

> [!NOTE]
> Il existe plusieurs différences lors de l’utilisation de Managed Instance :
>
> - FILESTREAM n’est pas pris en charge.
> - L’accès au système de fichiers local n’est pas pris en charge, mais est nécessaire pour certaines choses telles que les fichiers de trace.
> - La création d’un UDT depuis le chemin local n’est pas prise en charge.
> - L’authentification intégrée de Windows n’est pas prise en charge.
> - DTC n’est pas pris en charge.
> - Le compte `sa` n’est pas présent (le compte par défaut est appelé `cloudSA`).
> - L’erreur de jeton TDS (0xAA) retourne un nom de serveur incorrect.
> - Les caractères spéciaux dans les noms de base de données ne sont pas pris en charge.
> - ALTER DATABASE [nom_bd_1] MODIFY NAME = [nom_bd_2] n’est pas pris en charge.
> - Les messages d’erreur sont toujours affichés en anglais, quels que soient les paramètres de langue (à l’image d’Azure).

## <a name="131"></a>13.1

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ajoute la prise en charge d’[Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) et d’[Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md). | Ces nouvelles prises en charge sont disponibles lors de la connexion à Microsoft SQL Server version 2016 ou ultérieure. |
| Il existe des mots clés et attributs de regroupement de connexions, qui correspondent aux prises en charge d’Always Encrypted et d’Azure Active Directory. | Ces mots clés et attributs sont décrits dans [Regroupement de connexions prenant en charge le pilote dans ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="13"></a>13

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Ajoute la prise en charge de Microsoft SQL Server 2016. | Conserve les fonctionnalités du pilote ODBC version 11. |
| &nbsp; | &nbsp; |

## <a name="11"></a>11

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Contient de nouvelles fonctionnalités. | Consultez [Fonctionnalités de Microsoft ODBC Driver for SQL Server sur Windows](features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md). |
| Contient toutes les fonctionnalités fournies avec ODBC dans SQL Server 2012 Native Client. | &nbsp; |
| &nbsp; | &nbsp; |
