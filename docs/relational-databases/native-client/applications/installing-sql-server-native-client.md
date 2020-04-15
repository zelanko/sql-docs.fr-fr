---
title: Installation de SQL Server Native Client (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: markingmyname
ms.author: maghan
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4c6f7dba15a6c86839f7c0285fbb383920e18589
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302480"
---
# <a name="installing-sql-server-native-client"></a>Installation de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 est installé quand vous installez [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]. 
 
 Il n’y a pas de sqL Server 2016 Native Client. Pour plus d’informations, consultez [SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md). 
 
Vous pouvez également obtenir sqlncli.msi à partir de la page web de SQL Server 2012 Feature Pack. Pour télécharger la version la plus récente du SQL Server Native Client, rendez-vous chez [Microsoft® SQL Server® 2012 Feature Pack](https://www.microsoft.com/download/confirmation.aspx?id=29065). Si une version [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] précédente de Native Client plus tôt que SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 est également installée sur l’ordinateur, Native Client 11.0 sera installé côte à côte avec la version antérieure.  
  
 Les fichiers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli11.dll, sqlnclir11.rll et s11ch_sqlncli.chm) sont installés à l'emplacement suivant :  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Tous les paramètres du Registre appropriés pour le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sont définis dans le cadre de la procédure d'installation.  
  
 Les fichiers de bibliothèque et d'en-tête [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli.h et ssqlncli11.lib) sont installés à l'emplacement suivant :  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Outre l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un programme d'installation redistribuable nommé sqlncli.msi se trouve sur le disque d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], à l'emplacement suivant : `%CD%\Setup\`.  
  
 Vous pouvez distribuer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client par le biais de sqlncli.msi. Vous pouvez être amené à installer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lorsque vous déployez une application. Une façon d'installer plusieurs packages dans ce qui paraît à l'utilisateur être une installation unique consiste à utiliser la technologie des programmes de chaînage et d'amorçage. Pour plus d’informations, consultez [Création d’un package de programme d’amorçage personnalisé pour Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) et [Ajout de composants requis personnalisés](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Les versions x64 et Itanium de sqlncli.msi installent également la version 32 bits de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Si votre application vise une plateforme autre que celle sur laquelle elle a été développée, vous pouvez télécharger les versions de sqlncli.msi pour x64, Itanium et x86 à partir du Centre de téléchargement Microsoft.  
  
 Lorsque vous appelez sqlncli.msi, seuls les composants clients sont installés par défaut. Les composants du client sont des fichiers qui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prennent en charge l’exécution d’une application qui a été développée à l’aide de Native Client. Pour installer également les composants SDK, spécifiez `ADDLOCAL=All` dans la ligne de commande. Par exemple :  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Installation sans assistance  
 Si vous utilisez l'option /passif, /qn, /qb, ou /qr avec msiexec, vous devez également spécifier IACCEPTSQLNCLILICENSETERMS=YES, pour indiquer explicitement que vous acceptez les termes de la licence utilisateur final. Cette option doit être spécifiée en majuscules.  
  
## <a name="uninstalling-sql-server-native-client"></a>Désinstallation de SQL Server Native Client  
 Étant donné [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applications [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] telles que le serveur et les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] outils dépendent de Native Client, il est important de ne pas désinstaller native Client jusqu’à ce que toutes les applications dépendantes ne soient pas bloquées. Pour les utilisateurs fournisseurs avec un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avertissement que votre application dépend de Native Client, utilisez l’option d’installation APPGUID dans votre MSI, comme suit:  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 La valeur passée à APPGUID est votre code de produit spécifique. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Construire des applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [Rubriques de procédures relatives à l'installation](https://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
