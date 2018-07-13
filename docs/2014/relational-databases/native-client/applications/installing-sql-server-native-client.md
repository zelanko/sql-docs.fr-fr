---
title: Installation de SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
caps.latest.revision: 43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6eb3f153ad1fdbb3d7dc907d7c2cee7a2678080f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417568"
---
# <a name="installing-sql-server-native-client"></a>Installation de SQL Server Native Client
  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 est installé lorsque vous installez [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]. Il n'y a pas de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client. Pour plus d’informations, consultez [What ' s New in SQL Server Native Client](../sql-server-native-client.md). Vous pouvez également obtenir sqlncli.msi à partir de la page web de SQL Server 2012 Feature Pack. Pour télécharger la version la plus récente de SQL Server Native Client, accédez à [Microsoft® SQL Server® 2012 SP2 Feature Pack](http://www.microsoft.com/en-us/download/details.aspx?id=43339). Si une version précédente de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client antérieure à SQL Server 2012 est également installé sur l’ordinateur, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 sera installé côte à côte avec une version antérieure.  
  
 Les fichiers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli11.dll, sqlnclir11.rll et s11ch_sqlncli.chm) sont installés à l'emplacement suivant :  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Tous les paramètres du Registre appropriés pour le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sont définis dans le cadre de la procédure d'installation.  
  
 Les fichiers de bibliothèque et d'en-tête [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli.h et ssqlncli11.lib) sont installés à l'emplacement suivant :  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Outre l’installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans le cadre de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation, il existe également un programme d’installation redistribuable nommé sqlncli.msi, ce qui se trouve sur le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] disque d’installation dans l’emplacement suivant : `%CD%\Setup\`.  
  
 Vous pouvez distribuer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client par le biais de sqlncli.msi. Vous pouvez être amené à installer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lorsque vous déployez une application. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d’informations, consultez [création d’un Package de programme d’amorçage personnalisé pour Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) et [Ajout de composants requis personnalisés](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Les versions x64 et Itanium de sqlncli.msi installent également la version 32 bits de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Si votre application vise une plateforme autre que celle sur laquelle elle a été développée, vous pouvez télécharger les versions de sqlncli.msi pour x64, Itanium et x86 à partir du Centre de téléchargement Microsoft.  
  
 Lorsque vous appelez sqlncli.msi, seuls les composants clients sont installés par défaut. Les composants clients sont des fichiers qui prennent en charge l'exécution d'une application développée à l'aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Pour installer également les composants SDK, spécifiez `ADDLOCAL=All` dans la ligne de commande. Exemple :  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Installation sans assistance  
 Si vous utilisez l'option /passif, /qn, /qb, ou /qr avec msiexec, vous devez également spécifier IACCEPTSQLNCLILICENSETERMS=YES, pour indiquer explicitement que vous acceptez les termes de la licence utilisateur final. Cette option doit être spécifiée en majuscules.  
  
## <a name="uninstalling-sql-server-native-client"></a>Désinstallation de SQL Server Native Client  
 Étant donné que les applications telles que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] serveur et le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dépendent des outils [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, il est important de ne pas désinstaller [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client jusqu'à ce que toutes les applications dépendantes sont désinstallées. Pour les utilisateurs de fournisseur avec un avertissement indiquant que votre application dépend [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, utilisez l’option d’installation APPGUID dans votre fichier MSI, comme suit :  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 La valeur passée à APPGUID est votre code de produit spécifique. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Applications avec SQL Server Native Client](installing-sql-server-native-client.md)   
 [Rubriques de procédures relatives à l’installation](../../../sql-server/install/installation-how-to-topics.md)  
  
  
