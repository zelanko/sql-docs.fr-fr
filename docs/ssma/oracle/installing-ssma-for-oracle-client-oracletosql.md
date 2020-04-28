---
title: Installation de SSMA pour Oracle client (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: fc295e108357040617bf6bdaa1af61fada2c97ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68259680"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Installation du client SSMA pour le client Oracle (OracleToSQL)
Le client SSMA se compose des fichiers programme qui effectuent les tâches suivantes :  
  
-   Connectez-vous à une base de données Oracle.  
  
-   Connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Convertir des objets de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données Oracle en syntaxe.  
  
-   Chargez les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans.  
  
-   Migrer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]données vers.  
  
Cette rubrique décrit les conditions préalables à l’installation et les instructions pour l’installation de SSMA.  
  
## <a name="prerequisites"></a>Prérequis  
SSMA est conçu pour fonctionner avec Oracle 9 ou versions ultérieures, ainsi que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]toutes les éditions de.  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
-   Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou une version ultérieure.  
  
-   La [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4,0 ou une version ultérieure. La [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4,0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support du produit. Vous pouvez également l’obtenir à partir du [Centre de développement .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Oracle client 9,0 ou une version ultérieure, ainsi que la connectivité aux bases de données Oracle que vous souhaitez migrer. La version du client Oracle doit être identique à la version de la base de données Oracle, ou à une version ultérieure à celle-ci.  
  
    Vous pouvez installer le client Oracle à partir du support produit Oracle ou à partir du site Web Oracle. Pour plus d’informations sur la connectivité, consultez [connexion à Oracle Database &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Accès et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL DB où vous allez migrer des données et des objets de base de données. Pour plus d’informations, consultez [connexion à SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   4 Go de RAM recommandés.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Installation du client SSMA pour Oracle  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez la [page de téléchargement de Assistant Migration SQL Server](https://aka.ms/ssmafororacle).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation de avant de pouvoir installer SSMA.  
  
**Pour installer le client SSMA**  
  
1.  Double-cliquez sur SSMA pour Oracle *n*. Install. exe, où *n* est le numéro de Build.  
  
2.  Sur la page d'accueil, cliquez sur **Suivant**.  
  
    Si la configuration requise n’est pas installée, un message s’affiche pour indiquer que vous devez d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis, puis réexécutez le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final. Si vous acceptez, sélectionnez **J’accepte les termes du contrat de licence**, puis cliquez sur **suivant**.  
  
4.  Dans la page choisir le type d’installation, cliquez sur par **défaut**.  
  
5.  Cliquez sur **Installer**.  
  
> [!IMPORTANT]  
> 1.  Désinstallez toutes les versions antérieures de SSMA pour Oracle avant d’installer la nouvelle version.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft Assistant Migration SQL Server pour Oracle.  
  
En plus des fichiers programme SSMA, vous devez également installer SSMA pour Oracle extension Pack sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Installing SSMA Components on SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Migration de bases de données Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
