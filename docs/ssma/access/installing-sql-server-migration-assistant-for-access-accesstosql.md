---
title: L’installation de SQL Server Migration Assistant pour Access (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- installing SSMA
- instructions, installation
- instructions, upgrade
- licensing SSMA
- prerequisites for installing SSMA
- procedure, installation
- procedure, licensing
- procedure, upgrading
- removing SSMA
- Setup
- uninstalling SSMA
- upgrading SSMA
ms.assetid: dd50eebd-75df-4e0d-8c4d-88b511aae4c7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 128c83e0fd63b2724311aec046bdb9683c569a03
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740939"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>L’installation de SQL Server Migration Assistant pour Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour l’accès est installé à l’aide d’un Assistant basé sur le programme d’installation de Windows. Cette rubrique fournit des informations sur les conditions préalables d’installation, un lien vers la dernière version de SSMA et des instructions pour l’installation, la gestion des licences, la désinstallation et la mise à niveau SSMA.  
  
## <a name="prerequisites"></a>Prérequis  
Avant d’installer SSMA, assurez-vous que votre système répond aux exigences suivantes :  
  
-   Windows 7 ou une version ultérieure, ou Windows Server 2008 ou une version ultérieure.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 ou une version ultérieure.  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework version 4.0 ou une version ultérieure. Le .NET Framework version 4.0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du produit et en utilisant les informations contenues dans le [Microsoft .NET Guide](https://docs.microsoft.com/dotnet/framework/).
  
-   Accès à et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]base de données SQL Azure à laquelle vous effectuez la migration des objets de base de données et des données.  
  
-   Microsoft objet DAO (Data Access) version 12.0 ou 14.0 du fournisseur. Vous pouvez installer le fournisseur DAO à partir du produit Microsoft Office 2010/2007, ou téléchargez-le à partir du site web de Microsoft.  
  
-   Le SQL Server Native Access Client (SNAC) version 10.5 et versions ultérieures pour la migration vers SQL Azure. Vous pouvez obtenir la dernière version de SNAC de [Microsoft® SQL Server® 2008 R2 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 Go de RAM (recommandé).  
  
## <a name="installing-ssma"></a>Installation de SSMA  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez le [page de téléchargement de l’Assistant Migration de SQL Server](https://aka.ms/ssmaforaccess).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation avant que vous puissiez installer SSMA.

> [!IMPORTANT]  
> -   Veuillez désinstaller toutes les versions précédentes de SSMA pour Access avant d’installer la nouvelle version.  
  
**Pour installer SSMA**  
  
1.  Double-cliquez sur SSMA pour Access *n*.msi, où *n* est le numéro de build.  
  
2.  Dans la page d’accueil, cliquez sur **suivant**.  
  
    Si vous n’avez pas les composants requis installés, un message s’affiche indiquant que vous devez tout d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis et puis exécutez à nouveau le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final ; Si vous acceptez, cochez **J’accepte le contrat**, puis cliquez sur **suivant**.  
  
4.  Dans la page Choisir un Type d’installation, cliquez sur **standard**.  
  
5.  Cliquez sur **Installer**.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft SQL Server Migration Assistant pour l’accès.  
  
## <a name="uninstalling-ssma-for-access"></a>Désinstallation de SSMA pour Access  
Désinstaller SSMA à l’aide de **Ajout / Suppression de programmes** dans le panneau de configuration. N’oubliez pas que la désinstallation du programme ne supprime pas les fichiers de projet SSMA ou des fichiers journaux.  
  
**Pour désinstaller SSMA**  
  
1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis cliquez sur **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez **Microsoft SQL Server Migration Assistant pour Access**, puis cliquez sur **supprimer**.  
  
## <a name="upgrading-to-a-later-version"></a>La mise à niveau vers une version ultérieure  
Si vous souhaitez mettre à niveau vers une version ultérieure de SSMA pour Access, vous devez d’abord désinstaller SSMA pour Access et puis installer la version plus récente. Suivez les instructions de désinstallation de SSMA pour la section accès pour exécuter ce processus.  
  
Si vous ouvrez un projet créé dans une version antérieure de SSMA pour Access, SSMA vous demande si vous souhaitez convertir le projet vers la version plus récente. Cliquez sur **Oui** pour travailler avec le projet dans la version la plus récente de SSMA.  
  
## <a name="see-also"></a>Voir aussi  
[Préparation des bases de données Access pour la Migration](preparing-access-databases-for-migration-accesstosql.md)  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Liaison d’Applications Access vers SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
