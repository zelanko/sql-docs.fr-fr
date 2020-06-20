---
title: Installation de SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b93a38614800e1298894caa9c6d97c3f9353ac73
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85017357"
---
# <a name="installing-sql-server-native-client"></a>Installation de SQL Server Native Client
  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 est installé quand vous installez [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]. Il n'y a pas de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client. Pour plus d’informations, consultez [Nouveautés de SQL Server Native Client](../sql-server-native-client.md). Vous pouvez également obtenir sqlncli.msi à partir de la page web de SQL Server 2012 Feature Pack. Pour télécharger la version la plus récente de la SQL Server Native Client, accédez à [Microsoft ? SQL Server?? Feature Pack 2012 SP2](https://www.microsoft.com/download/details.aspx?id=43339). Si une version précédente de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client antérieure à SQL Server 2012 est également installée sur l'ordinateur, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 sera installé côte à côte avec la version antérieure.  
  
 Les fichiers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli11.dll, sqlnclir11.rll et s11ch_sqlncli.chm) sont installés à l'emplacement suivant :  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Tous les paramètres du Registre appropriés pour le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sont définis dans le cadre de la procédure d'installation.  
  
 Les fichiers de bibliothèque et d'en-tête [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli.h et ssqlncli11.lib) sont installés à l'emplacement suivant :  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Outre l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un programme d'installation redistribuable nommé sqlncli.msi se trouve sur le disque d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], à l'emplacement suivant : `%CD%\Setup\`.  
  
 Vous pouvez distribuer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client par le biais de sqlncli.msi. Vous pouvez être amené à installer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lorsque vous déployez une application. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d’informations, consultez [Création d’un package de programme d’amorçage personnalisé pour Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) et [Ajout de composants requis personnalisés](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Les versions x64 et Itanium de sqlncli.msi installent également la version 32 bits de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Si votre application vise une plateforme autre que celle sur laquelle elle a été développée, vous pouvez télécharger les versions de sqlncli.msi pour x64, Itanium et x86 à partir du Centre de téléchargement Microsoft.  
  
 Lorsque vous appelez sqlncli.msi, seuls les composants clients sont installés par défaut. Les composants clients sont des fichiers qui prennent en charge l’exécution d’une application développée à l’aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Pour installer également les composants SDK, spécifiez `ADDLOCAL=All` dans la ligne de commande. Par exemple :  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Installation sans assistance  
 Si vous utilisez l'option /passif, /qn, /qb, ou /qr avec msiexec, vous devez également spécifier IACCEPTSQLNCLILICENSETERMS=YES, pour indiquer explicitement que vous acceptez les termes de la licence utilisateur final. Cette option doit être spécifiée en majuscules.  
  
## <a name="uninstalling-sql-server-native-client"></a>Désinstallation de SQL Server Native Client  
 Étant donné que les applications telles que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Server et les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Outils dépendent de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, il est important de ne pas désinstaller [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client tant que toutes les applications dépendantes ne sont pas désinstallées. Pour les utilisateurs du fournisseur disposant d’un avertissement indiquant que votre application dépend de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, utilisez l’option d’installation APPGUID dans votre MSI, comme suit :  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 La valeur passée à APPGUID est votre code de produit spécifique. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications avec SQL Server Native Client](installing-sql-server-native-client.md)   
 [Rubriques de procédures relatives à l'installation](../../../sql-server/install/installation-how-to-topics.md)  
  
  
