---
title: Installation de Assistant Migration SQL Server pour Access (AccessToSQL) | Microsoft Docs
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
ms.openlocfilehash: cbbb7ed7a20937d9963af7080fb16be4f6c78da5
ms.sourcegitcommit: 59c09dbe29882cbed539229a9bc1de381a5a4471
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79111909"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Installation de Assistant Migration SQL Server pour Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Migration (SSMA) pour Access est installé à l’aide d’un assistant basé sur Windows Installer. Cette rubrique fournit des informations sur les conditions préalables à l’installation, un lien vers la dernière version de SSMA et des instructions pour l’installation, la gestion des licences, la désinstallation et la mise à niveau de SSMA.  
  
## <a name="prerequisites"></a>Prérequis  
Avant d’installer SSMA, assurez-vous que votre système répond aux exigences suivantes :  
  
-   Windows 7 ou une version ultérieure, ou Windows Server 2008 ou une version ultérieure.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou une version ultérieure.  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework version 4,0 ou une version ultérieure. La version 4,0 de .NET Framework est disponible sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le disque du produit et à l’aide des informations du [Guide de Microsoft .net](https://docs.microsoft.com/dotnet/framework/).
  
-   Accès et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure DB vers laquelle vous allez migrer des données et des objets de base de données.  
  
-   Microsoft Data Access Object (DAO) Provider version 12,0 ou 14,0. Vous pouvez installer le fournisseur DAO à partir de Microsoft Office produit 2010/2007 ou le télécharger à partir du site Web de Microsoft.  
  
-   Le SQL Server Native Access client (SNAC) version 10,5 et versions ultérieures pour la migration vers SQL Azure. Vous pouvez obtenir la dernière version de SNAC à partir de [Microsoft® SQL Server® 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272)  
  
-   4 Go de RAM (recommandé).  
  
## <a name="installing-ssma"></a>Installation de SSMA  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez la [page de téléchargement de Assistant Migration SQL Server](https://aka.ms/ssmaforaccess).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation de avant de pouvoir installer SSMA.

> [!IMPORTANT]  
> -   Désinstallez toutes les versions antérieures de SSMA pour l’accès avant d’installer la nouvelle version.  
  
**Pour installer SSMA**  
  
1.  Double-cliquez sur SSMA pour Access *n*. msi, où *n* est le numéro de Build.  
  
2.  Sur la page d'accueil, cliquez sur **Suivant**.  
  
    Si la configuration requise n’est pas installée, un message s’affiche pour indiquer que vous devez d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis, puis réexécutez le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final ; Si vous acceptez, sélectionnez **J’accepte le contrat**, puis cliquez sur **suivant**.  
  
4.  Dans la page choisir le type d’installation, cliquez sur par **défaut**.  
  
5.  Cliquez sur **Installer**.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft Assistant Migration SQL Server pour l’accès.  
  
## <a name="uninstalling-ssma-for-access"></a>Désinstallation de SSMA pour Access  
Désinstallez SSMA en utilisant **Ajout/suppression de programmes** dans le panneau de configuration. N’oubliez pas que la désinstallation du programme ne supprime pas les fichiers de projet ou les fichiers journaux SSMA.  
  
**Pour désinstaller SSMA**  
  
1.  Cliquez sur **Démarrer**, sur **Panneau de configuration**, puis sur **Ajout/Suppression de programmes**.  
  
2.  Sélectionnez **Assistant Migration Microsoft SQL Server pour l’accès**, puis cliquez sur **supprimer**.  
  
## <a name="upgrading-to-a-later-version"></a>Mise à niveau vers une version ultérieure  
Si vous souhaitez effectuer une mise à niveau vers une version ultérieure de SSMA pour Access, vous devez d’abord désinstaller SSMA pour accéder à, puis installer la version plus récente. Suivez les instructions de la section désinstallation de SSMA for Access pour terminer ce processus.  
  
Si vous ouvrez un projet créé dans une version antérieure de SSMA pour l’accès, SSMA vous demande si vous souhaitez convertir le projet vers la version la plus récente. Cliquez sur **Oui** pour travailler avec le projet dans la version plus récente de SSMA.  
  
## <a name="see-also"></a>Voir aussi  
[Préparation des bases de données Access pour la migration](preparing-access-databases-for-migration-accesstosql.md)  
[Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Liaison des applications Access à SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
