---
title: Installation de SSMA pour Sybase client (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8680685640b234e47f6e68d7fb802fc7e2f5d81c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029020"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>Installation du client SSMA pour Sybase (SybaseToSQL)
Le client SSMA se compose des fichiers programme utilisés pour se connecter à un serveur de base de données Sybase Adaptive Server Enterprise (ASE) et à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une instance de ou d’Azure SQL dB, convertir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des objets de base de données ASE vers ou une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe Azure SQL dB, charger les objets dans ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL dB, puis migrer les données vers ou Azure SQLDB.  
  
Cette rubrique décrit les conditions préalables à l’installation et les instructions pour l’installation de SSMA.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
SSMA est conçu pour fonctionner avec ASE 11.9.2 ou versions ultérieures, ainsi que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]toutes les éditions de.  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
-   Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou une version ultérieure.  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework version 4,0 ou une version ultérieure. Le .NET Framework version 4,0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support du produit. Vous pouvez également l’obtenir à partir du [Centre de développement .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Le fournisseur Sybase OLEDB/ADO.Net/ODBC et la connectivité au serveur de base de données Sybase ASE qui contient les bases de données que vous souhaitez migrer. Vous pouvez installer des fournisseurs à partir du support produit Sybase ASE. Pour plus d’informations sur la connectivité, consultez [connexion à Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Accès et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL DB où vous allez migrer des données et des objets de base de données. Pour plus d’informations, consultez [connexion à SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [connexion à Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 Go de RAM recommandés.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Installation du client SSMA pour Sybase  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez la [page de téléchargement de Assistant Migration SQL Server](https://aka.ms/ssmaforsybase).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation de avant de pouvoir installer SSMA.  
  
**Pour installer le client SSMA**  
  
1.  Double-cliquez sur SSMA pour Sybase *n*. Install. exe, où *n* est le numéro de Build.  
  
2.  Sur la page d'accueil, cliquez sur **Suivant**.  
  
    Si la configuration requise n’est pas installée, un message s’affiche pour indiquer que vous devez d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis, puis réexécutez le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final. Si vous acceptez, sélectionnez **J’accepte les termes du contrat de licence**, puis cliquez sur **suivant**.  
  
4.  Dans la page choisir le type d’installation, cliquez sur par **défaut**.  
  
5.  Cliquez sur **Installer**.  
  
> [!IMPORTANT]  
> 1.  Désinstallez toutes les versions antérieures de SSMA pour Sybase avant d’installer la nouvelle version.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft Assistant Migration SQL Server pour Sybase.  
  
En plus des fichiers programme SSMA, vous devez également installer SSMA pour le pack d’extension Sybase sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Installing SSMA Components on SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Migration de bases de données Sybase ASE vers SQL Server-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
