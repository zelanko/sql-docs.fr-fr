---
title: Installation de SSMA pour Sybase Client (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6cca10f2a54a70e91e46bb8b98e9799885b5f175
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740989"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>Installation du client SSMA pour Sybase (SybaseToSQL)
Le client SSMA comprend les fichiers de programme qui sont utilisés pour se connecter à un serveur de base de données Sybase Adaptive Server Enterprise (ASE) et une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL DB, convertir des objets de base de données ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la syntaxe de base de données SQL Azure, charger le d’objets en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, et migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQLDB.  
  
Cette rubrique fournit les conditions préalables d’installation et les instructions d’installation de SSMA.  
  
## <a name="prerequisites"></a>Prérequis  
SSMA est conçu pour fonctionner avec ASE 11.9.2 ou versions ultérieures et toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
-   Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 ou une version ultérieure.  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework version 4.0 ou une version ultérieure. Le .NET Framework version 4.0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support du produit. Vous pouvez également les obtenir à partir de la [centre de développement .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Le fournisseur de Sybase OLEDB/ADO.Net/ODBC et de la connectivité au serveur de base de données Sybase ASE qui contient les bases de données que vous souhaitez migrer. Vous pouvez installer des fournisseurs à partir du support produit de Sybase ASE. Pour plus d’informations sur la connectivité, consultez [connexion à Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Accès à et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure dans lequel vous effectuez la migration des objets de base de données et des données. Pour plus d’informations, consultez [connexion à SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)/[connexion à Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 Go de RAM recommandé.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Installation de SSMA pour Sybase Client  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez le [page de téléchargement de l’Assistant Migration de SQL Server](https://aka.ms/ssmaforsybase).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation avant que vous puissiez installer SSMA.  
  
**Pour installer le client SSMA**  
  
1.  Double-cliquez sur SSMA pour Sybase *n*. Install.exe, où *n* est le numéro de build.  
  
2.  Dans la page d’accueil, cliquez sur **suivant**.  
  
    Si vous n’avez pas les composants requis installés, un message s’affiche indiquant que vous devez tout d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis et puis exécutez à nouveau le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final. Si vous acceptez, cochez **J’accepte les termes du contrat de licence**, puis cliquez sur **suivant**.  
  
4.  Dans la page Choisir un Type d’installation, cliquez sur **standard**.  
  
5.  Cliquez sur **Installer**.  
  
> [!IMPORTANT]  
> 1.  Désinstallez toutes les versions précédentes de SSMA pour Sybase avant d’installer la nouvelle version.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft SQL Server Migration Assistant pour Sybase.  
  
Outre les fichiers de programme SSMA, vous devez également installer SSMA pour Sybase le Pack d’Extension sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [installation des composants SSMA sur SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
