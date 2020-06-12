---
title: Installation de SSMA pour le client DB2 (DB2ToSQL) | Microsoft Docs
description: En savoir plus sur les conditions préalables à l’installation de l’Assistant Migration SQL Server (SSMA) pour le client DB2 et sur l’installation de.
ms.prod: sql
ms.custom: ''
ms.date: 09/07/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7615f775a43da2853a0c98f8402f738e73dc8bb6
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293806"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Installation de SSMA pour le client DB2 (DB2ToSQL)

Le client SSMA se compose des fichiers programme qui effectuent les tâches suivantes :  
  
- Connectez-vous à une base de données DB2.  
  
- Connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
- Convertit les objets de base de données DB2 en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe.  
  
- Chargez les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
- Migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Cette rubrique décrit les conditions préalables à l’installation et les instructions pour l’installation de SSMA.  
  
## <a name="prerequisites"></a>Prérequis

SSMA est conçu pour fonctionner avec DB2 sur z/OS version 9,0 et 10,0 ou DB2 sur LUW version 9,8 et 10,1 ou versions ultérieures et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 ou versions ultérieures.  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
- Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou versions ultérieures.  
  
- La [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4,0 ou une version ultérieure. La [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4,0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support du produit. Vous pouvez également l’obtenir à partir du [Centre de développement .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
- Fournisseur Microsoft OLEDB pour DB2 version 5 ou version ultérieure, et connectivité aux bases de données DB2 que vous souhaitez migrer.  
  
- Accès et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL DB où vous allez migrer des données et des objets de base de données. Pour plus d’informations, consultez [connexion à SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
- 4 Go de RAM recommandés.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Fournisseur Microsoft OLEDB pour DB2  

Pour télécharger le fournisseur OLEDB pour DB2 version 6,0, accédez à [Microsoft® SQL Server® 2017 Feature Pack](https://www.microsoft.com/download/details.aspx?id=55992).

SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez la [page de téléchargement de Assistant Migration SQL Server](https://aka.ms/ssmafordb2).  
  
Après avoir téléchargé la dernière version, extrayez les fichiers d’installation afin de pouvoir installer SSMA.  
  
Pour installer le client SSMA :
  
1. Double-cliquez sur SSMA pour DB2 *n*.Install.exe, où *n* est le numéro de Build.  
  
2. Sur la page d’**accueil**, sélectionnez **Suivant**.  
  
   Si la configuration requise n’est pas installée, un message s’affiche pour indiquer que vous devez d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis, puis réexécutez le programme d’installation.  
  
3. Lisez le contrat de licence utilisateur final. Si vous acceptez, sélectionnez **J’accepte les termes du contrat de licence**, puis sélectionnez **suivant**.  
  
4. Dans la page **choisir le type d’installation** , sélectionnez **standard**.  
  
5. Sélectionnez **Installer**.  
  
> [!IMPORTANT]  
> Désinstallez toutes les versions antérieures de SSMA pour DB2 avant d’installer la nouvelle version.
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft Assistant Migration SQL Server pour DB2.  
  
## <a name="see-also"></a>Voir aussi

[Installation des composants SSMA sur SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Migration de bases de données DB2 vers SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
