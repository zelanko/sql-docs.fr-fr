---
title: Installer le pilote OLE DB pour SQL Server | Microsoft Docs
description: Installation et désinstallation du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 08f33d84ee8c035e1e1d3818e2a036f96af2a280
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989312"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installation d’OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Pour installer le pilote OLE DB pour SQL Server vous avez besoin du programme d’installation de msoledbsql. msi.
Exécutez le programme d’installation et effectuez vos sélections préférées. Le pilote OLE DB pour SQL Server peut être installé côte à côte avec les versions antérieures des fournisseurs Microsoft OLE DB.

Le pilote OLE DB pour les fichiers SQL Server (msoledbsql. dll, msoledbsqlr. rll) est installé `%SYSTEMROOT%\system32\` dans. En outre, le fichier msoledbsql. msi x64 installe les fichiers binaires 32 `%SYSTEMROOT%\SysWOW64\`bits dans.

> [!NOTE]  
> Tous les paramètres de registre appropriés pour le pilote OLE DB pour SQL Server sont effectués dans le cadre du processus d’installation.  

Le pilote OLE DB pour SQL Server fichiers de bibliothèque et d’en-tête (msoledbsql. h et msoledbsql. lib `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`) sont installés dans. En outre, le fichier msoledbsql. msi x64 installe les mêmes fichiers `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`dans.  

Vous pouvez distribuer OLE DB pilote pour SQL Server par le biais de msoledbsql. msi. Vous devrez peut-être installer OLE DB pilote pour SQL Server quand vous déployez une application. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d’informations, consultez [Création d’un package de programme d’amorçage personnalisé pour Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) et [Ajout de composants requis personnalisés](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
Le msoledbsql. msi x64 installe également la version 32 bits du pilote OLE DB pour SQL Server. Si votre application cible une plateforme autre que celle sur laquelle elle a été développée, vous pouvez télécharger les versions de msoledbsql. msi pour x64 et x86.

Quand vous appelez msoledbsql.msi, seuls les composants clients sont installés par défaut. Les composants clients sont des fichiers qui prennent en charge l’exécution d’une application développée avec OLE DB Driver pour SQL Server. Pour installer également les composants SDK, spécifiez `ADDLOCAL=All` dans la ligne de commande. Par exemple :  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Installation sans assistance  
 Si vous utilisez l’option /passive, /qn, /qb ou /qr avec msiexec, vous devez également spécifier IACCEPTMSOLEDBSQLLICENSETERMS=YES pour indiquer explicitement que vous acceptez les termes de la licence utilisateur final. Cette option doit être spécifiée en majuscules.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Installation du pilote OLE DB pour SQL Server en tant que dépendance  
Il est important de ne pas désinstaller OLE DB pilote pour SQL Server tant que toutes les applications dépendantes ne sont pas désinstallées. Pour fournir aux utilisateurs un avertissement indiquant que votre application dépend de OLE DB pilote pour SQL Server, utilisez l’option d’installation APPGUID dans votre MSI, comme suit:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

La valeur passée à APPGUID est votre code de produit spécifique. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application.
L’option APPGUID nécessite l’exécution du programme d’installation à partir d’une invite de commandes avec élévation de privilèges.

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
