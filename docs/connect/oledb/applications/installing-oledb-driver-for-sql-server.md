---
title: L’installation du pilote OLE DB pour SQL Server | Documents Microsoft
description: Installation et désinstallation du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: e31904372a2850d27a3fad9158dad6bbd763dc6d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installation du pilote OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Pour installer le pilote OLE DB pour SQL Server, vous devez les installer msoledbsql.msi.
Exécutez le programme d’installation et effectuez vos sélections par défaut. Le pilote OLE DB pour SQL Server peut être installé côte à côte avec les versions antérieures des fournisseurs OLE DB de Microsoft.

Pour télécharger la version la plus récente du pilote OLE DB pour SQL Server, allez à [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=56730).

Le pilote OLE DB pour SQL Server (msoledbsql.dll, msoledbsqlr.rll) sont installés à l’emplacement suivant :  

`%SYSTEMROOT%\system32\`  

> [!NOTE]  
> Tous les paramètres de Registre appropriés pour le pilote OLE DB pour SQL Server sont effectuées dans le cadre du processus d’installation.  

Le pilote OLE DB pour les fichiers d’en-tête et de la bibliothèque SQL Server (msoledbsql.h et msoledbsql.lib) sont installés dans l’emplacement suivant :  

`%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\180\SDK`  

Vous pouvez distribuer le pilote OLE DB pour SQL Server via msoledbsql.msi. Vous devrez peut-être installer le pilote OLE DB pour SQL Server lorsque vous déployez une application. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d’informations, consultez [création d’un Package de programme d’amorçage personnalisé pour Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) et [Ajout de composants requis personnalisés](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
Le x64 msoledbsql.msi installe également la version 32 bits du pilote OLE DB pour SQL Server. Si votre application cible une plateforme autre que celui qu’il a été développée, vous pouvez télécharger des versions de msoledbsql.msi pour x64 et x86.

Lorsque vous appelez msoledbsql.msi, seuls les composants clients sont installés par défaut. Le client sont des composants sont des fichiers qui prennent en charge l’exécution d’une application qui a été développée à l’aide du pilote OLE DB pour SQL Server. Pour installer également les composants SDK, spécifiez `ADDLOCAL=All` dans la ligne de commande. Par exemple :  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

## <a name="silent-install"></a>Installation sans assistance  
 Si vous utilisez l’option, /qn, /qb ou option de /qr avec msiexec, vous devez également spécifier IACCEPTMSOLEDBSQLLICENSETERMS = Oui, pour indiquer explicitement que vous acceptez les termes du contrat de licence utilisateur final. Cette option doit être spécifiée en majuscules.  

## <a name="uninstalling-ole-db-driver-for-sql-server"></a>Désinstallation du pilote OLE DB pour SQL Server  
Étant donné que les applications telles que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] serveur et le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] outils dépendent du pilote OLE DB pour SQL Server, il est important de ne pas désinstaller le pilote OLE DB pour SQL Server jusqu'à ce que toutes les applications dépendantes sont désinstallées. Pour fournir aux utilisateurs un message d’avertissement que votre application dépend de pilote OLE DB pour SQL Server, vous devez utiliser l’option d’installation APPGUID dans votre fichier MSI, comme suit :  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

La valeur passée à APPGUID est votre code de produit spécifique. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application.  

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
