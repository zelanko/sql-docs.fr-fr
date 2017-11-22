---
title: "L’installation de SSMA pour Sybase Client (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
caps.latest.revision: "18"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 04357499b0ac47f8fa130ceb117946cbeeba1378
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>L’installation de SSMA pour Sybase Client (SybaseToSQL)
Le client SSMA comprend les fichiers de programme qui sont utilisés pour se connecter à un serveur de base de données Sybase Adaptive Server Enterprise (ASE) et une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou Azure SQL DB, convertir les objets de base de données ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou une syntaxe de base de données SQL Azure, chargez les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure, puis migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQLDB d’Azure.  
  
Cette rubrique fournit les conditions préalables d’installation et les instructions pour l’installation de SSMA.  
  
## <a name="prerequisites"></a>Conditions préalables  
SSMA est conçu pour fonctionner avec ASE 11.9.2 ou versions ultérieures et toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur répond aux exigences suivantes :  
  
-   Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3.1 ou une version ultérieure.  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework version 4.0 ou version ultérieure. Le .NET Framework version 4.0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] support du produit. Vous pouvez également obtenir de le [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Le fournisseur de Sybase OLEDB/ADO.Net/ODBC et de la connectivité avec le serveur de base de données Sybase ASE qui contient les bases de données que vous souhaitez migrer. Vous pouvez installer des fournisseurs à partir du support produit de Sybase ASE. Pour plus d’informations sur la connectivité, consultez [la connexion à Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Accès à et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure où vous migrerez des objets de base de données et les données. Pour plus d’informations, consultez [la connexion à SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [La connexion à la base de données SQL Azure &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 Go de RAM est recommandé.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>L’installation de SSMA pour Sybase Client  
SSMA est téléchargeable sur le Web. Pour télécharger la version la plus récente, consultez le [page de téléchargement de l’Assistant Migration SQL Server](http://aka.ms/ssmaforsybase).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation avant de pouvoir installer SSMA.  
  
**Pour installer le client SSMA**  
  
1.  Double-cliquez sur SSMA pour Sybase  *n* . Install.exe, où  *n*  est le numéro de build.  
  
2.  Dans la page d’accueil, cliquez sur **suivant**.  
  
    Si vous n’avez pas les composants requis installés, un message s’affiche indiquant que vous devez d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis et puis exécutez à nouveau le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final. Si vous acceptez, cochez **J’accepte les termes du contrat de licence**, puis cliquez sur **suivant**.  
  
4.  Dans la page Choisir un Type d’installation, cliquez sur **standard**.  
  
5.  Cliquez sur **Installer**.  
  
> [!IMPORTANT]  
> 1.  Désinstallez toutes les versions précédentes de SSMA pour Sybase avant d’installer la nouvelle version.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft SQL Server Migration Assistant pour Sybase.  
  
Outre les fichiers de programme SSMA, vous devez également installer SSMA pour Sybase Extension Pack sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Pour plus d’informations, consultez [l’installation des composants de SSMA sur SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Migration Sybase ASE bases de données SQL Server : base de données SQL Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
