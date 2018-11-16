---
title: Installation de SSMA pour DB2 Client (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1d479c8f7de1c9d7463e57f37f9e8588c9bc68b6
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666498"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Installation de SSMA pour DB2 Client (DB2ToSQL)
Le client SSMA comprend les fichiers de programme qui effectuent les tâches suivantes :  
  
-   Se connecter à une base de données DB2.  
  
-   Connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Convertir des objets de base de données DB2 à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe.  
  
-   Charger les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Cette rubrique fournit les conditions préalables d’installation et les instructions d’installation de SSMA.  
  
## <a name="prerequisites"></a>Prérequis  
SSMA est conçu pour fonctionner avec DB2 sur z/OS version 9.0 et 10.0 ou DB2 sur LUW version 9.8 et 10.1 ou versions ultérieures et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
-   Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 ou une version ultérieure.  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4.0 ou une version ultérieure. Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4.0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support du produit. Vous pouvez également les obtenir à partir de la [centre de développement .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Fournisseur Microsoft OLEDB pour DB2 version 5 ou une version ultérieure et la connectivité aux bases de données DB2 que vous souhaitez migrer.  
  
-   Accès à et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure dans lequel vous effectuez la migration des objets de base de données et des données. Pour plus d’informations, consultez [connexion à SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
-   4 Go de RAM recommandé.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Fournisseur Microsoft OLEDB pour DB2  
Pour télécharger le fournisseur OLEDB pour DB2 version 5.0, accédez à [Microsoft® SQL Server® 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=42295).  
  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez le [page de téléchargement de l’Assistant Migration de SQL Server](https://aka.ms/ssmafordb2).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation avant que vous puissiez installer SSMA.  
  
**Pour installer le client SSMA**  
  
1.  Double-cliquez sur SSMA pour DB2 *n*. Install.exe, où *n* est le numéro de build.  
  
2.  Dans la page d’accueil, cliquez sur **suivant**.  
  
    Si vous n’avez pas les composants requis installés, un message s’affiche indiquant que vous devez tout d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis et puis exécutez à nouveau le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final. Si vous acceptez, cochez **J’accepte les termes du contrat de licence**, puis cliquez sur **suivant**.  
  
4.  Dans la page Choisir un Type d’installation, cliquez sur **standard**.  
  
5.  Cliquez sur **Installer**.  
  
> [!IMPORTANT]  
> 1.  Désinstallez toutes les versions précédentes de SSMA pour DB2 avant d’installer la nouvelle version.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft SQL Server Migration Assistant pour DB2.  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Bases de données de migration de DB2 vers SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
