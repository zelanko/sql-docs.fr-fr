---
title: Installation de SSMA pour MySQL client (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9dcdeaff1c4782453a9fd57cc709e17ad3200d28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086826"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Installation de SSMA pour MySQL Client (MySQLToSQL)
Le client SSMA pour MySQL se compose des fichiers programme qui effectuent les tâches suivantes :  
  
-   Connectez-vous à une base de données MySQL.  
  
-   Connectez-vous à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de ou SQL Azure.  
  
-   Convertissez les objets de base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données MySQL en objets ou SQL Azure.  
  
-   Chargez les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans ou SQL Azure.  
  
-   Migrer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données vers ou SQL Azure.  
  
Cette rubrique décrit les conditions préalables à l’installation et fournit des instructions pour l’installation du client SSMA pour MySQL.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
SSMA pour MySQL est conçu pour fonctionner avec MySQL 4,1 ou versions ultérieures, ainsi que toutes les éditions de SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016, SQL Server 2017 et Azure SQL DB.  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
-   Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou une version ultérieure.  
  
-   La [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4,0 ou une version ultérieure. La [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4,0 est disponible sur le support du produit SQL Server. Vous pouvez également l’obtenir à partir du [Centre de développement .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Pilote ODBC 5,1 MySQL et connectivité avec les bases de données MySQL que vous souhaitez migrer. Vous pouvez installer MySQL à partir du site Web MySQL. Pour plus d’informations sur la connectivité, consultez [connexion à MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Accès et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de SQL Server où vous allez migrer les données et les objets de base de données. Pour plus d’informations, consultez [connexion à SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   En cas de SQL Azure des projets, accédez à l’instance de base de données SQL Azure et accédez-y aux autorisations nécessaires pour effectuer la migration des objets et des données de base de données. Pour plus d’informations, consultez [connexion à la base de données SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   4 Go de RAM recommandés.  
  
## <a name="installing-ssma-for-mysql-client"></a>Installation de SSMA pour MySQL Client  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez la [page de téléchargement de Assistant Migration SQL Server](https://aka.ms/ssmaformysql).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation avant de pouvoir installer SSMA.  
  
**Pour installer le client SSMA**  
  
1.  Double-cliquez sur SSMA pour MySQL *n*. Install. exe, où *n* est le numéro de Build.  
  
2.  Sur la page d'accueil, cliquez sur **Suivant**.  
  
    Si la configuration requise n’est pas installée, un message s’affiche pour indiquer que vous devez d’abord installer les composants requis. Assurez-vous que vous avez installé toutes les conditions préalables avant d’exécuter à nouveau le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final. Si vous acceptez, sélectionnez **J’accepte les termes du contrat de licence**, puis cliquez sur **suivant**.  
  
4.  Dans la page choisir le type d’installation, cliquez sur par **défaut**.  
  
5.  Cliquez sur **Installer**.  
  
> [!IMPORTANT]  
> 1.  Désinstallez toutes les versions antérieures de SSMA pour MySQL avant d’installer la nouvelle version.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft Assistant Migration SQL Server pour MySQL.  
  
Sur une machine Windows 64 bits, le produit est installé dans C:\Microsoft Assistant Migration SQL Server pour MySQL.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données MySQL vers SQL Server-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
