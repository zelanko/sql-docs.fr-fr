---
title: Installer le pilote OLE DB pour SQL Server | Microsoft Docs
description: Installation et désinstallation d’OLE DB Driver pour SQL Server. Pour installer OLE DB Driver pour SQL Server, vous avez besoin du programme d’installation msoledbsql.msi
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
ms.openlocfilehash: 1edd1c6e7a118e152fc1f8e85203434347061da5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007063"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installation d’OLE DB Driver pour SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Pour installer OLE DB Driver pour SQL Server, vous avez besoin du programme d’installation msoledbsql.msi.
Exécutez le programme d’installation et effectuez vos sélections. OLE DB Driver pour SQL Server peut être installé en parallèle avec les versions antérieures des fournisseurs Microsoft OLE DB.

Les fichiers OLE DB Driver pour SQL Server (msoledbsql.dll, msoledbsqlr.rll) sont installés dans `%SYSTEMROOT%\system32\` . En outre, msoledbsql.msi x64 installe les fichiers binaires 32 bits dans `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Tous les paramètres du Registre appropriés pour OLE DB Driver pour SQL Server sont définis dans le cadre de la procédure d'installation.  

Les fichiers bibliothèque et d'en-tête OLE DB Driver pour SQL Server (msoledbsql.h et msoledbsql.lib) sont installés dans `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`. En outre, le fichier msoledbsql.msi x64 installe les mêmes fichiers dans `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`.  

Vous pouvez distribuer OLE DB Driver pour SQL Server via msoledbsql.msi. Vous pouvez être amené à installer OLE DB Driver pour SQL Server lorsque vous déployez une application. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d’informations, consultez [Création d’un package de programme d’amorçage personnalisé pour Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) et [Ajout de composants requis personnalisés](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
msoledbsql.msi x64 installe également la version 32 bits d’OLE DB Driver pour SQL Server. Si votre application vise une plateforme autre que celle sur laquelle elle a été développée, vous pouvez télécharger les versions de msoledbsql.msi pour x64 et x86.

Quand vous appelez msoledbsql.msi, seuls les composants clients sont installés par défaut. Les composants clients sont des fichiers qui prennent en charge l’exécution d’une application développée avec OLE DB Driver pour SQL Server. Pour installer également les composants SDK, spécifiez `ADDLOCAL=All` dans la ligne de commande. Par exemple :  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Installation sans assistance  
 Si vous utilisez l’option /passive, /qn, /qb ou /qr avec msiexec, vous devez également spécifier IACCEPTMSOLEDBSQLLICENSETERMS=YES pour indiquer explicitement que vous acceptez les termes de la licence utilisateur final. Cette option doit être spécifiée en majuscules.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Installer OLE DB Driver pour SQL Server comme dépendance  
Il est important de ne pas désinstaller OLE DB Driver pour SQL Server tant que toutes les applications dépendantes n’ont pas été désinstallées. Pour avertir les utilisateurs que votre application dépend d’OLE DB Driver pour SQL Server, utilisez l'option d'installation APPGUID dans votre fichier MSI, comme suit :  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

La valeur passée à APPGUID est votre code de produit spécifique. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application.
L’option APPGUID nécessite l’exécution du programme d’installation à partir d’une invite de commandes avec élévation de privilèges.

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
