---
title: Installer le pilote OLE DB pour SQL Server | Microsoft Docs
description: Installation et la désinstallation du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
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
manager: craigg
ms.openlocfilehash: 7dc75f03ac806c50008f7b536e7a1f0ed037d496
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602219"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installation d’OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Pour installer le pilote OLE DB pour SQL Server, vous avez besoin de programme d’installation msoledbsql.msi.
Exécutez le programme d’installation et effectuez vos sélections par défaut. Le pilote OLE DB pour SQL Server peut être installé côte à côte avec les versions antérieures des fournisseurs OLE DB de Microsoft.

Le pilote OLE DB pour les fichiers de SQL Server (msoledbsql.dll, msoledbsqlr.rll) sont installés dans `%SYSTEMROOT%\system32\` . En outre, le x64 msoledbsql.msi installe les fichiers binaires 32 bits dans `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Tous les paramètres du Registre appropriés pour le pilote OLE DB pour SQL Server sont effectuées dans le cadre du processus d’installation.  

Le pilote OLE DB pour les fichiers d’en-tête et de la bibliothèque SQL Server (msoledbsql.h et msoledbsql.lib) sont installés dans `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`. En outre, le x64 msoledbsql.msi installe les mêmes fichiers dans `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`.  

Vous pouvez distribuer OLE DB Driver pour SQL Server via msoledbsql.msi. Vous devrez peut-être installer le pilote OLE DB pour SQL Server lorsque vous déployez une application. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d’informations, consultez [Création d’un package de programme d’amorçage personnalisé pour Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) et [Ajout de composants requis personnalisés](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
Le x64 msoledbsql.msi installe également la version 32 bits du pilote OLE DB pour SQL Server. Si votre application cible une plateforme autre que celui qu’il a été développée, vous pouvez télécharger les versions de msoledbsql.msi pour x64 et x86.

Quand vous appelez msoledbsql.msi, seuls les composants clients sont installés par défaut. Les composants clients sont des fichiers qui prennent en charge l’exécution d’une application développée avec OLE DB Driver pour SQL Server. Pour installer également les composants SDK, spécifiez `ADDLOCAL=All` dans la ligne de commande. Exemple :  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Installation sans assistance  
 Si vous utilisez l’option /passive, /qn, /qb ou /qr avec msiexec, vous devez également spécifier IACCEPTMSOLEDBSQLLICENSETERMS=YES pour indiquer explicitement que vous acceptez les termes de la licence utilisateur final. Cette option doit être spécifiée en majuscules.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Installation du pilote OLE DB pour SQL Server en tant que dépendance  
Il est important de ne pas désinstaller le pilote OLE DB pour SQL Server jusqu'à ce que toutes les applications dépendantes sont désinstallées. Pour fournir aux utilisateurs un message d’avertissement que votre application repose sur OLE DB Driver pour SQL Server, utilisez l’option d’installation APPGUID dans votre fichier MSI, comme suit :  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

La valeur passée à APPGUID est votre code de produit spécifique. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application.
L’option APPGUID requiert le programme d’installation en cours d’exécution à partir d’une invite de commandes avec élévation de privilèges.

## <a name="see-also"></a> Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
